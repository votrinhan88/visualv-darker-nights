# visualv-darker-nights
VisualV Darker Nights mods for Grand Theft Auto V | v1.70.1 | [gta5-mods.com](https://www.gta5-mods.com/misc/less-darker-nights)

Features:
+ Makes beautiful dark nights based on [VisualV](https://www.gta5-mods.com/misc/visualv) and [Darker Nights](https://www.lcpdfr.com/downloads/gta5mods/datafile/40491-darker-nights/).
+ Wide range of darker settings (-40% to 80%) between VisualV and Darker Nights.
+ Tested on GTA V 1.70.1 (except for the brighter versions).

Installation:
1. Always make backup first!
2. Download [VisualV](https://www.gta5-mods.com/misc/visualv).
3. Extract VisualV.oiv separately (NOT install by OpenIV) and copy their timecycle .xml files in update/update.rpf/common/data/timecycles to mods/update/update.rpf/common/data/timecycles.
    + This is because we use VisualV as a base, and certain weather are not modified by Darker Nights.
3. Drop all (10 .xml) files located in <this mod>/composed/<your-choice>% into mods/update/update.rpf/common/data/timecycles.
    + Darker Nights modified these files, but I have toned down the darkness.
    + Recommended settings: 80% darker-nights - 20% visualv.

Uninstallation: (Reverting to vanilla values)
1. Download [VisualV](https://www.gta5-mods.com/misc/visualv).
2. Extract Original files.oiv separately (NOT install by OpenIV) and copy their timecycle .xml files in update/update.rpf/common/data/timecycles to mods/update/update.rpf/common/data/timecycles.

<b>Changlog:</b>
+ v1.70.1: Add brighter nights (-20%, -40%)

Advanced customization:
+ I included the miniconda environment details to run Python code in ./environment.yml. You can reproduce the environment and mess around with the Python notebook ./main.ipynb as you like for more custom editting.
    + More on setting up [miniconda](https://docs.anaconda.com/miniconda/install/).
    + Once conda is installed: run from cmd `conda env create -f environment.yml` to install environment.
    + Activate from cmd with `conda activate darker-nights`.
+ Custom interpolation values:
    + Put the VisualV timecycle files into ./inputs/visualv and Darker Nights timecycle files into ./inputs/darker-nights (please download from original sources - I cannot include them here).
    + Modify the values in INPUTS_MIX_COEFFS in main.ipynb.
        + E.g.: If you want 65% Darker Nights and 35% VisualV, change it to ```INPUTS_MIX_COEFFS = {'darker-nights': 0.65, 'visualv': 0.35}```.
    + Make sure the coefficients sum to 1.
    + Run the script --> Outputs files are at .outputs/.
+ Combining multiple (>2) timecycle configs:
    + Put the timecycle files from each source into their corresponding folder ./inputs/<source>. (Else errors will be raised.)
    + Make sure all folders have the same list of .xml files. (Else errors will be raised.)
    + Modify the values in INPUTS_MIX_COEFFS in main.ipynb.
    + Run the script --> Outputs files are at .outputs/
    + E.g.: If you want 30% vanilla, 20% modA, 50% modB:
        + Put the files in ./inputs/vanilla, ./inputs/modA, ./inputs/modB.
        + Change it to ```INPUTS_MIX_COEFFS = {'vanilla': 0.3, 'modA': 0.2, 'modB': 0.5}```.
+ Some tags does not exist in every input files. In this case:
    + 2 input sources: the script automatically picks only the available sources 
    + \>2 input sources: the script automatically picks only the available sources, and the mixing coefficients INPUTS_MIX_COEFFS automatically gets normalized so that the coefficients of available sources sums to 1.
        + E.g.: with INPUTS_MIX_COEFFS = {'vanilla': 0.3, 'modA': 0.2, 'modB': 0.5} but vanilla and modA has a certain tag that modB does not have, the coefficients for such tag gets normalized to {'vanilla': 0.6, 'modA': 0.4}.
+ Logs are inside the console when running ./main.ipynb and at ./log.log.

Disclaimer:
+ This is a toned-down version of Darker Nights 1.4 by Gelse16 combined with VisualV by _CP_ & robi29. Most credits go to them. I only write the Python codes to compose interpolated values.
+ I am not able to assist with advanced modders. But the code is clean and easy-to-follow, please try to figure it out yourself.