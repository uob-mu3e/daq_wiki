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