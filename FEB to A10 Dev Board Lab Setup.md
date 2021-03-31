# Requirements #
* Front End Board
* [A10 Dev Board](https://www.terasic.com.tw/cgi-bin/page/archive.pl?Language=English&CategoryNo=231&No=970#https://www.terasic.com.tw/attachment/archive/970/image/DE5a-Net_45d.jpg)
* [Si5338 Clk board](https://www.silabs.com/documents/public/user-guides/Si5338-EVB.pdf)
* Root 6 with CXX > 14
* Linux Kernel > 4.12
* Quartus
* TODO: Detector stuff?

# Installation Hardware #
* Programm the Clk board in such a way that it has two synchronized clk outputs (each having 125MHz). One needs to be a differential LVDS clk and the other one needs to be a CMOS output.
(TODO: upload a configuration file here)
* Connect the two clks to the FPGA Boards (TODO: add picture from the lab with the connections)
* Remark: for the testing the A10 board standalone one can just connect the two SMA ports on the board (TODO: picture)
* TODO: what is missing?


# Installation Software #
* `git clone git@bitbucket.org:mu3e/online.git`
* `git checkout DEV-BRANCH`
* `git submodule update —init —-recursive`
* `mkdir build`
* `cd build`
* `cmake ..`
* `make`
* `make install`

# Compile Hardware #
* A basic A10 board file is stored at https://seafile.rlp.net/d/399ebc0f7e5b49d59522/ at `Mu3e Firmware/SWB/ SWB_debug_sof_file/top_signaltap.sof`
* 
* To compile the firmware 

# Start MIDAS #
* `source set_env.sh`
* `source start_daq.sh`
* Now a lot of Midas Frontends are starting. You should be able to see them now under localhost:8080
 (TODO: add picture)
* Open a new Terminal and navigate to the build directory and again `source set_env.sh`



```
#!c++
TMupixDQHistogramManager::CreateHistograms()
TMupixDQHistogramManager::UpdateHistograms(MupixHit& hit)

```
* If you want to create a new histogram type (TNewHistogram), you need to create a new class like the TMupixDQHistogram and store it in data_objects/histograms. Than you need to add the new histogram to IntRunAnalysis (moduls.h).

```
#!c++

class IntRunAnalysis: public TARunObject
{
public:

   ...

   // histograms produced by this module
   TNewHistogram m_TNewHistogram;

};
```

* To create your histogram you need to change the function:
```
#!c++

IntRunAnalysis::BeginRun(TARunInfo* runinfo){
   printf("IntRunAnalysis::BeginRun, run %d, file %s\n", runinfo->fRunNo, runinfo->fFileName.c_str());
   
   // select new ROOT directory
   TDirectory* d_root=make_or_get_dir("", gDirectory);
   TDirectory* d=make_or_get_dir("YOUR_NEW_HISTOGRAM", d_root);
   d->cd();
   // YOUR_NEW_HISTOGRAM
   // ...
}
```
* To fill your histogram you need to change the IntRunAnalyzer again:

```
#!c++

TAFlowEvent* IntRunAnalysis::AnalyzeFlowEvent(TARunInfo* runinfo, TAFlags* flags, TAFlowEvent* flow)
{
   // New Histogram
   // crap your physics event
   MupixDataFlow* pixelFlow = flow->Find<MupixDataFlow>();
   // Update Histograms
   // loop over hits in container
   pixelFlow->DataContainer.ForEachHit([&](MupixHit& hitPix)->int{
      m_TNewHistogram.UpdateHistograms(hitPix);
      return 0;
   });
}
```