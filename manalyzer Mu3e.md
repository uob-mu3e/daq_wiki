# Framework #
![framework-1.png](https://bitbucket.org/repo/7zKBgbq/images/2796880107-framework-1.png)

# MIDAS Display #
![screenshot_20210308_140008.png](https://bitbucket.org/repo/7zKBgbq/images/404226720-screenshot_20210308_140008.png)

![screenshot_20210308_140806.png](https://bitbucket.org/repo/7zKBgbq/images/2183843815-screenshot_20210308_140806.png)

# Quick-Start Histograms/Analysis #
* Follow docs/midas.md to setup the analyzer
* You can add histograms to existing classes like TMupixDQHistograms.cpp. Therefore you need to change the functions:
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

# IntRunAna #
* At the moment (19.07.2021) use branch midas_to_root
* In ``analyzer/analyzer/config/config.json`` the default setup is for converting the midas file to a flat root file with the branches:   
```
#!c++
TBranch* runID = tree->Branch("runID", &m_runID);
TBranch* MIDASEventID = tree->Branch("MIDASEventID", &m_MIDASEventID);
TBranch* col = tree->Branch("col", &m_col);
TBranch* row = tree->Branch("row", &m_row);
TBranch* fpgaID = tree->Branch("fpgaID", &m_fpgaID);
TBranch* chipID = tree->Branch("chipID", &m_chipID);
TBranch* tot = tree->Branch("tot", &m_tot);
TBranch* hitTime = tree->Branch("hitTime", &m_hitTime);
TBranch* subHeaderTime = tree->Branch("subHeaderTime", &m_subHeaderTime);
```
* For getting the working chips removed one needs to get the current mask file (in csv format) from https://docs.google.com/spreadsheets/d/1MLfoeoRalqG3xdOlihH__vh-Nz2ZcfqS7bcGl2PiqWE/edit#gid=0 and convert this to a json file with analyzer/scripts/chip_masking_csv_to_json.py
* For converting the file to root create the folder root_output_files and run ./analyzer/analyzer_mu3e midas_file
* For a quick analysis one can use the python script analyzer/scripts/chip_time_cor.py