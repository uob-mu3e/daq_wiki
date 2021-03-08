# Framework #
![framework-1.png](https://bitbucket.org/repo/7zKBgbq/images/2796880107-framework-1.png)

# MIDAS Display #
![screenshot_20210308_140008.png](https://bitbucket.org/repo/7zKBgbq/images/404226720-screenshot_20210308_140008.png)

![screenshot_20210308_140806.png](https://bitbucket.org/repo/7zKBgbq/images/2183843815-screenshot_20210308_140806.png)

# Quick-Start Histograms/Analysis #
* follow docs/midas.md
* Change analyzer/analyzer/data_objects/histograms/src/TMupixDQHistograms.cpp for adding histograms
```
#!c++
TMupixDQHistogramManager::CreateHistograms()
TMupixDQHistogramManager::UpdateHistograms(MupixHit& hit)

```
* If you want to create a new histogram type than you need to create a new class like the TMupixDQHistogram and place the creation in the IntRunAnalysis. You can also change the folder with the make_or_get_dir function:
```
#!c++

IntRunAnalysis::BeginRun(TARunInfo* runinfo){
  printf("IntRunAnalysis::BeginRun, run %d, file %s\n", runinfo->fRunNo, runinfo->fFileName.c_str());
  
	// select correct ROOT directory
	TDirectory* d_root=make_or_get_dir("", gDirectory);
	TDirectory* d=make_or_get_dir("Pixel_DQ_histograms", d_root);
	d->cd();
	// PIXEL create histograms
	// DQ Histograms
	if ( pixelDQHistograms ) {
		m_Pixel_DQ_Histo.SetnLayer(nPixelLayer);
		m_Pixel_DQ_Histo.SetnPixelPerLayer(nPixelPerLayer);
		m_Pixel_DQ_Histo.CreateHistograms();
	}

        TDirectory* d_root=make_or_get_dir("", gDirectory);
	TDirectory* d=make_or_get_dir("YOUR_NEW_HISTOGRAM", d_root);
	d->cd();
	// YOUR_NEW_HISTOGRAM
        // ...
}
```