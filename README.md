# EMTFAnalyzer
Analysis tools for EMTF

To setup the NTuple maker:

Log into lxplus
setenv SCRAM_ARCH slc6_amd64_gcc630 (or export SCRAM_ARCH=slc6_amd64_gcc630)
cmsrel CMSSW_10_4_0
cd CMSSW_10_0_0/src
cmsenv
git cms-init
git remote add cms-sw git@github.com<mailto:git@github.com>:cms-sw/cmssw.git
git fetch cms-sw
git cms-addpkg DataFormats/L1TMuon
git cms-addpkg EventFilter/L1TRawToDigi
git cms-addpkg L1Trigger/L1TMuon
git cms-addpkg L1Trigger/L1TMuonEndCap

git remote add abrinke1
git@github.com<mailto:git@github.com>:abrinke1/cmssw.git
git fetch abrinke1
git cms-merge-topic -u abrinke1:EMTF_ALCT_CLCT_info
scram b clean
scram b -j 6

git clone https://github.com/Nik-Menendez/NTuple-Maker.git
cd EMTFAnalyzer/
scram b clean
scram b -j 6

cd .. (Into the CMSSW source folder)
scram b clean
scram b -j 6

cd EMTFAnalyzer/NTupleMaker/



The file used to run the NTuple Maker on MC is test/RunTrackFinder_MC_NTuple.py
Edit that file on lines 64 and 69 to choose the input file. And line 244 to choose the output directory.

To run the NTuple Maker on Monte Carlo:

cmsRun test/RunTrackFinder_MC_NTuple.py
