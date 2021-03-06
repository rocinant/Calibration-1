# Kalibr


The toolbox Kalibr is from Github ethz-asl/kalibr, more details can be found on [Wiki](https://github.com/ethz-asl/kalibr/wiki). Here shows how to run the demo Camera-IMU calibration Using dynamic Dataset.


 
## Install
### Using the CDE package (only 64bit systems)

To remove the necessity of installing ROS and building the toolbox from source, a CDE package is provided that packs the toolbox and all its dependencies in a chroot-like environment. To install this package follow these steps:
1.Download the most recent package from the [Downloads](https://github.com/ethz-asl/kalibr/wiki/downloads) page.
2.Extract the archive using:
> tar xfvz kalibr.tar.gz

##  Run
###  Input
The tool must be provided with the following input:
>--bag filename.bag

1,ROS bag containing the image and IMU data
>--cam camchain.yaml

2. intrinsic and extrinsic calibration parameters of the camera system. The output of the multiple-camera-calibration tool can be used here. (see YAML formats)
    
>--imu imu.yaml

3.contains the IMU statistics and the IMU's topic (see YAML formats)
> --target target.yaml
    
4.the calibration target configuration (see Cailbration targets)
###  Output
The calibration will produce the following output files:

>report-imucam-%BAGNAME%.pdf

1.Report in PDF format. Contains all plots for documentation.
> results-imucam-%BAGNAME%.txt

 2.Result summary as a text file.
>camchain-imucam-%BAGNAME%.yaml

3.Results in YAML format. This file is based on the input camchain.yaml with added transformations (and optionally time shifts) for all cameras with respect to the IMU. Please check the format on the YAML formats page.

## Test
### Using dynamic Dataset
An example using a sample dataset

Download the dataset from the  [Downloads](https://github.com/ethz-asl/kalibr/wiki/downloads) page and extract **dynamic.rar**. The archive will contain the bag, calibration target and IMU configuration file.

The calibration can be started with:

>kalibr_calibrate_imu_camera --target april_6x6.yaml --cam camchain.yaml --imu imu_adis16448.yaml --bag dynamic.bag --bag-from-to 5 45

NOTE1: Because there are shocks in the dataset (sensor pick-up/lay-down), only the data between 5 to 45 s is used.
NOTE2: If **dynamic.rar** is extracted in other folder, add datasets'path before each extracted data.


 