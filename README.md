# COSS

 * [Project Description](#project-description)
 * [Input Data](#input-data)
 * [Output Data](#output-data)
 * [Downloads](#downloads)
 * [Usage](#usage)
 
---
## Project Description

COSS is a user-friendly spectral library search tool capable of processing large spectral libraries and supporting multiple file formats. COSS is developed in Java and hence it is platform independent. COSS uses external subsystems for file reading and writing. Next to file io subsystems there are three main processes: preprocessing, feature extraction and matching. All processes are organized and implemented in a modular fashion to facilitate future upgrades. 

[Go to top of page](#coss)

---
## Input Data
COSS supports the following spectral file format for query (experimental) spectra.
 - Mascot Generic Format: mgf
 - NIST spectral library format: msp
 - Institute of System Biology (ISB): mzXML
 - HUPO Proteomics Standards Initiative file format (PSI): mzData
 - ISB and PSI joint format: mzML
 - SEQUEST: dta
 - pkl
 - ms2
 
Accepted spectral library file formats are mgf and msp.

[Go to top of page](#coss)

---
## Output Data
Users can export the result in excel. The output table contains 15 columns.

| Parameter  | Description        |
|------------|--------------------|
| Title | Title of the spectrum (for msp file, Name is used as title) |
| Library | Describes weather the library is true library or decoy |
| Scan num. | Scan number |
| Sequence | Peptide sequence from the matched library spectrum |
| Prec. Mass (M/Z) | Precursor mass of query spectrum |
| Charge | Charge of query specrum |
| Score | Search score |
| Validation | Validation, either 1% FDR or %5 FDR |
| #filteredQuerypeaks | Query peaks after filtering the spectrum under 100Da mass window |
| #filteredLibraryPeaks | Library peaks after filtering spectrum under 100Da mass window |
| SumIntQuery | Sum of peak intensities in filtered query spectrum |
| SumIntLib | Sum of peak intensities in filtered library spectrum |
| #MatchedPeaks | Number of matched peaks found in query and library spectrua being matched |
| MatchedIntQuery | Sum of peak intensities of query spectrum that have a match in library spectrum |
| MatchedIntLib | Sum of peak intensities of library spectrum that have a match in query spectrum |

It is also possible to save results in .cos format. This allows users to re-import previous results for visualization.

[Go to top of page](#coss)

---
## Downloads

Download the latest version of COSS  <a href="http://genesis.ugent.be/maven2/com/compomics/COSS/1.0/COSS-1.0.zip" onclick="trackOutboundLink('usage','download','coss','http://genesis.ugent.be/maven2/com/compomics/COSS/1.0/.zip'); return false;">here</a>.  

COSS can be run with the user-friendly GUI or through the CLI. 

[Go to top of page](#coss)

---
## Usage
### GUI
- Download COSS from the provided link and unzip it.
- On Windows you can run COSS by double clicking the COSS-X.Y.jar file. COSS can also be started from the command line using the following command:
```
$java -jar COSS-X.Y.jar
```
*X.Y stands for the version number (eg. COSS-1.1.jar)  
Make sure Java is installed on your machine.*
	
- Parameter Setting: Select and fill all required parameters.
- Decoy generation: It is recommended to add decoy spectra to your spectral library for result validation. If your library does not contain decoy spectra, these can be added with COSS. COSS has two algorithms to generate decoy spectra. Click the GenerateDecoy menu and select the algorithm to generate the decoy spectra (which will be equal in size to your spectra library) and concatenate the decoys to your library.
- Configuring File Reader: Click "Config Spec. Reader". At this time, the system disables the "Configure Reader" and "Start Seach" buttons until it is finished with the configuration. 
- Searching: Click "Start Searching", COSS starts searching and displays the status on the progress bar. The left-hand side window shows information of the query file. It also visualizes the spectra.
- Result: To see the results, click on the Result tab from the main window. The upper table lists the experimental spectra while the lower table lists the top 10 matched spectra for the selected experimental spectrum. An interactive spectrum comparison view is presented at the bottom with the selected experimental spectrum (red) mirrored with the selected matched library spectrum (blue).

### CLI
Command line searching is possible in COSS with the following commands:
```
java -jar COSS-X.Y.jar targetSpectraFile librarySpectraFile    
```
or                    
```
java -jar COSS-X.Y.jar targetSpectraFile librarySpectraFile precursorMassTolerance(PPM) fragmentTolerance(Da.) 
```
or
```
java -jar COSS-X.Y.jar targetSpectraFile librarySpectraFile precursorMassTolerance(PPM) fragmentTolerance(Da.) maxNumberofCharge
```
Decoy spectra can be generated and appended with the following command:
```
java -jar COSS-X.Y.jar -d librarySpectraFile
```
*X.Y stands for the version number (eg. COSS-1.1.jar)  
Make sure Java is installed on your machine.*

[Go to top of page](#coss)

---
| Java | Maven | Netbeans | 
|:--:|:--:|:--:|
|[![java](http://genesis.ugent.be/uvpublicdata/image/java.png)](http://java.com/en/) | [![maven](http://genesis.ugent.be/uvpublicdata/image/maven.png)](http://maven.apache.org/) | [![netbeans](https://netbeans.org/images_www/visual-guidelines/NB-logo-single.jpg)](https://netbeans.org/)

[Go to top of page](#coss)
