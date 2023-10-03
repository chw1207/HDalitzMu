# Higgs Dalitz muon channel analysis
<img src="https://render.githubusercontent.com/render/math?math=H\rightarrow\gamma^*\gamma\rightarrow ll\gamma"> is a rare Higgs decay. This repository is for the muon channel of Higgs Dalitz decay(<img src="https://render.githubusercontent.com/render/math?math=l=\mu">) analysis. 

## Usage
The ntuples were produced by the [ggNtuplizer](https://github.com/cmkuo/ggAnalysis/tree/106X). Signal MC ntuples need to be skimmed to filtered out the events with (<img src="https://render.githubusercontent.com/render/math?math=m_{\mu\mu} > 50 GeV">) first. 
```bash
sh runSkim.sh
```

The main analysis is implemented by the program `xAna.C`. To process the data and MC for each era, you can execute the following commands
```bash
# For Data
root -l -b -q runAna_Data_UL2016.C
root -l -b -q runAna_Data_UL2017.C
root -l -b -q runAna_Data.C

# For MC
root -l -b -q runAna_MC_UL2016preVFP.C
root -l -b -q runAna_MC_UL2016postVFP.C
root -l -b -q runAna_MC_UL2017.C 
root -l -b -q runAna_MC_UL2017_IsoMu.C 
root -l -b -q runAna_MC.C

# You can also submit all the processes to the background 
sh runAll.sh
```

To produce the table containing the [AMS](https://www.pp.rhul.ac.uk/~cowan/stat/medsig/medsigNote.pdf), resolution, and expected yields for each category, the program `runSignificance.C` can be used.
```bash
# For MuPho categories
root -l -b -q runSignificance.C\(0\)

# For IsoMu categories
root -l -b -q runSignificance.C\(1\)
```

