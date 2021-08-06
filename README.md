# ICOS_ATC_anomaly_detection_Jupyter

ICOS_ATC_anomaly_detection 

The file ADA_main.ipynb can be used for extracting synoptic scale and seasonal anomalies from ICOS CO2 time series.  Currently the code is set up to download the existing L2 and NRT data from a user-specified station from the ICOS data portal. The user has the option to upload their own station data if they would like to use pre-L2 data (not available from the data portal). Pre-L2 and L2 data up to May 30, 2020 are provided for the OPE station along with the L1 (NRT) data from June 1 to September 27, 2020. The code will concatenate the L2 and NRT datasets into one file and then apply the CCGvu package (Thoning et al., 1989) to extract a harmonic fit to the data, a polynomial function, and a smooth curve defined as the polynomial plus a short-term residual filter. The difference between the smooth curve and the harmonic is stored as delta-C.

The delta-C values are then used to defined "envelopes" around the CCGvu harmonic curve. These are defined as a daily dataset of 2x the standard deviation of all delta-C values within 90 (+45/-45) days of the current calendar date over all years in the record. A smooth curve is then fit to the daily data, and any segment where the smooth curve is outside the 2-sigma envelope is considered to be a measurement anomaly.

This procedure is performed at 30 and 90 days. For the 30-day curve, anomalies are considered to represent synoptic scale events. For the 90-day curve, they are considered to represent seasonal anomalies. Note that the name of the station, the dates, and the paths may need to be changed from those in the example.
