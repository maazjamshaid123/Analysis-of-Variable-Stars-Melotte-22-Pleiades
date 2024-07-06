# Melotte 22 Cluster Analysis

## Overview
Melotte 22, also known as the Pleiades or Seven Sisters, is a prominent open star cluster known to contain variable stars. This project focuses on analyzing the variability and membership probability of selected variable stars within the cluster.

## Selected Variable Stars
The following 12 variable stars exhibit variability in their brightness, often due to extrinsic factors like eclipsing binaries:

- 0102
- 0120
- 0157
- 0164
- 0173
- 0233
- 0320
- 0476
- 0522
- 0605
- 0916
- 1084

## Membership Probability
The probability of these stars being members of the Melotte 22 cluster has been determined using various methods such as proper motion studies, radial velocity measurements, and photometric studies. The membership probabilities for the selected stars are listed below:

| Star ID | Reference | Probability |
|---------|-----------|-------------|
| 0102    | 473       | 0.90        |
| 0120    | 438       | 0.97        |
| 0157    | 438       | 0.23        |
| 0164    | 438       | 0.91        |
| 0173    | 473       | 0.67        |
| 0233    | 438       | 0.91        |
| 0320    | 473       | 0.72        |
| 0476    | 438       | 0.97        |
| 0522    | 473       | 0.85        |
| 0605    | 438       | 0.79        |
| 0916    | 473       | 0.90        |
| 1084    | 438       | 0.88        |

## Data Retrieval from VizieR

To obtain data for the Pleiades cluster from the Gaia DR3 catalog, follow these steps:

1. Go to the [VizieR website](https://vizier.u-strasbg.fr/viz-bin/VizieR).
2. In the "Search Tables" field, enter "Pleiades" and click "Go."
3. Search for the Gaia catalog, specifically the I/355/gaiadr3 catalog.
4. Select the catalog by checking the box next to it.
5. Scroll down to the "Construct your Query" section.
6. Enter the Right Ascension (RA) and Declination (Dec) coordinates for the center of the Pleiades cluster (e.g., RA: 03h 47m 00s, Dec: +24° 07' 00").
7. Enter a radius of 30 arcminutes in the radius field.
8. Choose the output format (e.g., CSV).
9. Click "Run" to execute the query.
10. Download the data file from the provided link.

## Cross-Matching with CDS

To cross-match data from the Gaia DR3 catalog with the cluster catalog using the CDS cross-match service, follow these steps:

1. Access the [CDS cross-match service](http://cdsxmatch.u-strasbg.fr/).
2. In the "Select your main table" dropdown, choose "Gaia DR3."
3. Upload a CSV file containing the coordinates (α, δ) of the stars you want to analyze.
4. Define the criteria for matching stars, selecting a radius of 60 arcminutes (as the cluster's diameter is 120 arcminutes).
5. Run the cross-match to find stars with a high probability of cluster membership.

## Analysis Results

### Stars with High Membership Probability
The following stars have a membership probability of 70% or higher, based on proper motion and parallax data:

| Source | Proper Motion RA | Proper Motion DE | Parallax | Membership Probability |
|--------|-------------------|------------------|----------|------------------------|
| 0      | 19.879            | -45.151          | 7.335    | 1                      |
| 1      | 20.623            | -44.131          | 7.2541   | 1                      |
| 2      | 19.173            | -45.845          | 7.1444   | 1                      |
| 3      | 19.93             | -45.884          | 7.3186   | 1                      |
| ...    | ...               | ...              | ...      | ...                    |
| 99     | 20.394            | -45.783          | 7.2805   | 1                      |

### Average Calculations
- **Average Proper Motion RA:** 20.008882978723403
- **Average Proper Motion DE:** -45.34851063829788
- **Average Parallax:** 7.308825531914894

### Code Snippet for Average Calculation
```python
pAMa = pleiades_data["pAMa"]
selected_indices = np.where(pAMa >= 0.7)[0]
sources = pleiades_data["Source"][selected_indices]
source_pm_ra_cosdec = pleiades_data["pmRA"][selected_indices].dropna()
source_pm_dec = pleiades_data["pmDE"][selected_indices].dropna()
source_parallax = pleiades_data["Plx"][selected_indices].dropna()
