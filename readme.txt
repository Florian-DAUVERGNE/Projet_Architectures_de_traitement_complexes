This is the open access MovePort dataset published with our paper entitled: 
"MovePort: Multimodal Dataset of EMG, IMU, MoCap and Insole Pressure for Analyzing Abnormal Movements and Postures in Rehabilitation Training".

When using our dataset, please cite the above article.



Part 1. File Structure

The exported data is stored in the "data" folder. The file structure is as follows:
data:
├─1
│  …………
└─25
    ├─back
    ├─forward
    ├─halfsquat
    ├─still
    ├─ground_gait (only available for the subject with spastic paraplegia)
    ├─treadmill_normal
    ├─treadmill_leghigh
    └─treadmill_dragging
where 1-25 is the index of each participant.





Part 2. Introduction of Experimental Paradigm

Experiment 1: Participants are required to perform specific gaits on a treadmill.
	Normal Gait (treadmill_normal): This mode includes three speeds of normal walking.
	Low Speed: Walking at a speed of 1 km/h.
	Medium Speed: Walking at a speed of 2 km/h.
	High Speed (customizable): Walking at a speed of 3-4 km/h, with the specific speed chosen by the participants for comfortable brisk walking.

	Dragging Gait (dragging): Simulating a patient's difficulty in lifting their legs with a speed of 1 km/h, representing an abnormal gait.
	High Leg Lift Gait (leghigh): Simulating excessively high leg lifts due to overstimulation (e.g. the epidural/functional electrical stimulation used in neurorehabilitation) with a speed of 2 km/h, representing an abnormal gait.

Experiment 2: Participants are required to perform specific body postures on ground
	Standing still（still）： Standard standing without any special movements.
	Forward Lean（forward）：Participants lean their bodies forward to simulate a forward-weighted posture.
	Backward Lean (back): Participants tilt their bodies backward to simulate a backward-weighted posture.
	Half Squat (halfsquat): Participants perform a half-squat to simulate a posture with inadequate support.







Part 3.	Introduction to Data Files

The naming format of data files is: modality_SegmentIndex.csv/avi
Descriptions of different data modalities are as follows:
	Electromyography (EMG) Data
Modality Name: emg
Data Size: 16*nframe
Sampling Rate: 2000 Hz
Unit: Microvolts
Each column of data contains raw data from 8 muscles on each leg, named as: L/R_muscle_abbreviation

Muscle abbreviations are as follows:
Vlat - Vastus Lateralis
RF - Rectus Femoris
ST - Semitendinosus
TA - Tibialis Anterior
MG - Medial Gastrocnemius
LG - Lateral Gastrocnemius
SOL - Soleus
IL - Iliopsoas

	Inertial Measurement Unit (IMU) Data
Modality Name: imu
Data Size: 54*nframe
Sampling Rate: 100 Hz
Units: Acceleration (M/s²), Angular Velocity (°/s), Euler Angles (°)
Each column of data contains 9-axis data from 6 body positions of IMU, named as: Position_axis

Positions of IMU sensors are as follows:
Head, Waist (near Pelvis)
L_H - Left Hand/Wrist, R_H - Right Hand/Wrist
L_F - Left Foot, R_F - Right Foot

Axis names are as follows：
Acc_X/Y/Z - Acceleration along x, y, and z axes
Gyr_X/Y/Z - Angular velocity along x, y, and z axes
Roll, Pitch, Yaw - Euler angles along three axes

	Insole Pressure Sensors (IPS) Data
Modality Name: ips
Data Size: 682*nframe
Sampling Rate: 60 Hz
Unit: psi
Each column contains a 682-length vector of feet pressure distribution (measured by two 31*11 electrode arrays, one array per feet; 1-341 dimensions: left foot; 342-682: right foot). 230 out of the 341 electrodes (each side) are active, with other electrodes giving 0 values. But we still give a 31*11 (=341) electrode array so that the data can be represented as a 2-dimensional matrix.

Modality Name: Center of Pressure (COP)
COP data are highly correlated with IPS data.
Data Size: 6*nframe
Sampling Rate: 60 Hz
Units: N, m
Each column contains total pressure values, and (in certain files) we also give the calculated pressure center coordinates of the feet, named as follows:
L/R_Force: Total pressure on the left/right foot
L/R_cop_x: X-axis coordinates of the pressure center on the left/right foot
L/R_cop_y: Y-axis coordinates of the pressure center on the left/right foot
Note: The coordinate system used for the center of pressure is consistent with the one used for the motion capture system.

	Motion Capture (MoCap) Data
Modality Name: mocap
Data Size: 78*nframe
Sampling Rate: 100 Hz
Unit: meters
Each column contains three-dimensional spatial coordinates of 26 motion capture markers, named as: marker_name_x/y/z
Specific marker names are explained as follows:


Marker Label	Location Description
IJ		Jugular Notch, located above the sternum handle, where the left and right clavicles connect
C7 		7th cervical vertebra, located at the highest protrusion behind the bent neck
RA		Right Acromion, the flat part above the right shoulder joint's front and outside
LA 		Left Acromion, the flat part above the left shoulder joint's front and outside
T8 		8th thoracic vertebra, counting up to the 8th rib, connected to it is the 8th thoracic vertebra
R_LHE 		Right Elbow Joint, outside
R_RS 		Right Wrist Joint, outside
L_LHE 		Left Elbow Joint, outside
L_RS   		Left Wrist Joint, outside
M_PSIS		Posterior Superior Iliac Spine, located at the rear end of the iliac crest
R_IAS		Right Anterior Superior Iliac Spine, located at the front of the right iliac crest
R_FTC		Right Greater Trochanter, at the junction of the right femoral neck and body on the upper outside
L_IAS		Left Anterior Superior Iliac Spine, located at the front of the left iliac crest
L_FTC		Left Greater Trochanter, at the junction of the left femoral neck and body on the upper outside
R_FLE		Right Knee Joint, outside
R_FME		Right Knee Joint, inside
R_TTC		Right Tibial Plateau
R_LM		Right Ankle Joint, outside
R_CAL		Right Heel
R_MH1		The 1st toe of the right foot
L_FlE		Left Knee Joint, outside
L_FME		Left Knee Joint, inside
L_TTC		Left Tibial Plateau
L_LM		Left Ankle Joint, outside
L_CAL		Left Heel
L_MH1		The 1st toe of the left foot

Note: Data is missing for some participants. Specific missing data is as follows:
Participants 18, 19, 20 and 24: data of the "leaning forward" body posture are not available. 
Participant 21: data of the "leaning forward" body posture and normal gait at low-speed are not available. 
Participant 22: data of the "leaning back" body posture are not available.  
Participant 23: data of the "leaning forward" and "half-squat" body postures are not available. 
