## **E-Nose Dataset for Multi-Component Liquid Condiment Concentration Prediction**
### Overview
This repository provides an electronic nose (E-nose) dataset collected using a self-built gas sensing system for concentration prediction of mixed liquid condiments.
The sensing platform consists of:

- An 8-sensor metal oxide semiconductor (MOS) gas sensor array
- Peripheral control circuits
- Gas sampling and delivery system

The dataset focuses on three common liquid condiments:

- Rice vinegar
- Cooking wine
- Soy sauce

### Experimental Conditions
Different concentration combinations were prepared and measured under controlled laboratory conditions.
During data acquisition:

- Ambient temperature was maintained at 23 ± 2 °C
- Relative humidity was maintained at 50 ± 3%

The controlled environment helps improve measurement consistency and reduce the influence of temperature and humidity fluctuations on the responses of the MOS sensor array.

### Electronic Nose System
The gas sensor array consists of:

1. MP3B
2. TGS2620
3. MP801
4. WSP2110
5. TGS2609
6. TGS2603
7. TGS2602
8. TGS2600

Sensor signals were acquired using an ADS1256 analog-to-digital converter:

- ADC Model: ADS1256
- Resolution: 24-bit
- Channels: 8 single-ended channels (4 differential channels)

A DC air pump was employed to provide a stable and continuous airflow throughout the measurement process.

### Measurement Protocol
Gas flow paths were automatically switched using solenoid valves during data acquisition.
Each measurement cycle consisted of four sequential stages:

1. Sample chamber cleaning: 10 s
2. Sensor chamber cleaning: 30 s
3. Baseline acquisition: 30 s
4. Sample exposure and acquisition: 60 s

Total cycle duration:

130 seconds

Only the baseline and sample acquisition stages are included in the released dataset.
Therefore, each sample contains:

- 30 s baseline data
- 60 s sensing-response data

Total recorded duration per sample:

90 seconds

At a sampling frequency of 5 Hz, each sample contains:

90 × 5 = 450 time points

for each of the eight sensor channels.
### Dataset Statistics
### Single-Component Dataset
The single-component dataset contains measurements of individual condiments at concentration levels from 10% to 100% with a 10% interval.
A shared 0% concentration sample is represented by pure water and serves as the zero-concentration reference for all three condiments.
Concentration levels:

- 0% (pure water)
- 10%
- 20%
- 30%
- 40%
- 50%
- 60%
- 70%
- 80%
- 90%
- 100%

For each concentration level:

50 independent samples were collected.

Total number of samples:

- Rice vinegar: 500 samples
- Cooking wine: 500 samples
- Soy sauce: 500 samples
- Pure water: 50 samples

Total single-component samples:

1,550 samples
### Multi-Component Dataset
The multi-component dataset contains all possible binary and ternary mixtures under the following constraint:

Rice Vinegar (%) + Cooking Wine (%) + Soy Sauce (%) ≤ 100%

Concentration levels are generated with a 10% interval.
Pure single-component combinations are excluded because they are already included in the single-component dataset.
For each concentration combination:

30 independent samples were collected.

Total multi-component samples:

7,650 samples
### Complete Dataset

- Single-component: 1550 samples
- Multi-component: 7650 samples
- Total: 9200 samples

### Data Format
The dataset is provided in two formats:
### CSV Format
Example filename:

20%米醋30%料酒00%酱油1号样本.csv

represents:

- Rice Vinegar: 20%
- Cooking Wine: 30%
- Soy Sauce: 0%
- Sample No.1

Characteristics:

- Includes column headers
- Comma-separated values
- Human-readable
- Suitable for direct import into spreadsheet and data analysis software

Data structure:

|Column|Description|
|-|-|
|时间(s)|Time(s)|
|MP3B传感器(V)|MP3B(V)|
|TGS2620传感器(V)|TGS2620(V)|
|MP801传感器(V)|MP801(V)|
|WSP2110传感器(V)|WSP2110(V)|
|TGS2609传感器(V)|TGS2609(V)|
|TGS2603传感器(V)|TGS2603(V)|
|TGS2602传感器(V)|TGS2602(V)|
|TGS2600传感器(V)|TGS2600(V)|

### TXT Format
Example filename:

2-3-0-1.txt

Encoding rule:

- First number: rice vinegar concentration level
- Second number: cooking wine concentration level
- Third number: soy sauce concentration level
- Fourth number: sample index

For example:

2-3-0-1.txt

corresponds to:

- 20% rice vinegar
- 30% cooking wine
- 0% soy sauce
- Sample No.1

Characteristics:

- No column headers
- Space-separated values
- Compact storage format
- Data content identical to the CSV files

Data structure:

|Column|Description|
|-|-|
|1|Time(s)|
|2|MP3B(V)|
|3|TGS2620(V)|
|4|MP801(V)|
|5|WSP2110(V)|
|6|TGS2609(V)|
|7|TGS2603(V)|
|8|TGS2602(V)|
|9|TGS2600(V)|

### Dataset Organization
### TXT Dataset Structure
The TXT dataset is organized into subdirectories according to concentration combinations.
Example:
```
SINGLE/
├── 0-5-0/
│   ├── 0-5-0-1.txt
│   ├── 0-5-0-2.txt
│   └── ...
│
├── 0-0-2/
│   ├── 0-0-2-1.txt
│   └── ...
MIXED/
├── 1-2-3/
│   ├── 1-2-3-1.txt
│   ├── 1-2-3-2.txt
│   └── ...
```
Directory names encode concentration combinations:

RiceVinegar-CookingWine-SoySauce

File names follow the format:

RiceVinegar-CookingWine-SoySauce-SampleIndex.txt
### CSV Dataset Structure
The CSV dataset is stored without concentration-specific subdirectories.
Example:
```
SINGLEcsv/
├── 00%米醋00%料酒20%酱油43号样本.csv
├── 00%米醋00%料酒30%酱油12号样本.csv
└── ...
MIXEDcsv/
├── 00%米醋10%料酒10%酱油15号样本.csv
├── 20%米醋30%料酒00%酱油1号样本.csv
└── ...
```
The concentration labels are directly encoded in the file names.

The CSV and TXT datasets contain identical sensor measurements and labels. The only differences are file naming conventions and the presence of column headers in CSV files.
