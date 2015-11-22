---
title: "Codebook template"
author: "Antonio Menor Campos"
date: "22-11-2015"
output:
  html_document: 
    keep_md: yes
---

## Project Description
This is a project about Human Activity Recognition using smartphones. There are 30 subjects performing some activities (walking, walking upstairs, etc.) while carrying an smartphone (the smartphone has inertial sensors so we can get information about their movements)

##Study design and data processing
The study have been designed with a group of 30 volunteers (age between 19-48 years). Each of them performed six activities (WALKING, WALKING-UPSTAIRS, WALKING-DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone. 

###Collection of the raw data
As the smartphone has an accelerometer and a gyroscope, we captured 3-axial linear acceleration, and 3-axial angular velocity at a constant rate of 50HZ. All of this has been video-recorded in order to label the data. 

###Notes on the original (raw) data 
The raw data has been randomly partitioned into two sets: one of them with the 70% of the volunteers (train) and the rest is the tests data.

##Creating the tidy datafile

###Guide to create the tidy data file
The steps to get the tidy dataset:

 1. Load the files
 2. Clean and prepare the data
 3. Merges the training and the test sets to create one data set
 4. Extracts the measurements on the mean and standard deviation for each measurement
 5. Create a new and independent data set with the average of each variable
 
###Cleaning of the data
Short, high-level description of what the cleaning script does. [link to the readme document that describes the code in greater detail]()

Once the files are loaded, I change some column names and, as there were some duplicate columns in the features.txt file, I fixed it. I combine the dataset (first the test data, and second the train data) in a new data set (it has all the information: test + train). 

With the new dataset I get the tydi dataset that we were looking for: I group by subject and activity in order to get the mean of every variable. This dity dataset was written in a txt file, and submited.


##Description of the variables in the tiny_data.txt file
General description of the file:
Dimensions of the dataset: 180 x 68
Observations: 180
Variables: 68

1                          subject

2                         activity

3              1 tBodyAcc-mean()-X

4              2 tBodyAcc-mean()-Y

5              3 tBodyAcc-mean()-Z

6          41 tGravityAcc-mean()-X

7          42 tGravityAcc-mean()-Y

8          43 tGravityAcc-mean()-Z

9         81 tBodyAccJerk-mean()-X

10        82 tBodyAccJerk-mean()-Y

11        83 tBodyAccJerk-mean()-Z

12          121 tBodyGyro-mean()-X

13          122 tBodyGyro-mean()-Y

14          123 tBodyGyro-mean()-Z

15      161 tBodyGyroJerk-mean()-X

16      162 tBodyGyroJerk-mean()-Y

17      163 tBodyGyroJerk-mean()-Z

18          201 tBodyAccMag-mean()

19       214 tGravityAccMag-mean()

20      227 tBodyAccJerkMag-mean()

21         240 tBodyGyroMag-mean()

22     253 tBodyGyroJerkMag-mean()

23           266 fBodyAcc-mean()-X

24           267 fBodyAcc-mean()-Y

25           268 fBodyAcc-mean()-Z

26       345 fBodyAccJerk-mean()-X

27       346 fBodyAccJerk-mean()-Y

28       347 fBodyAccJerk-mean()-Z

29          424 fBodyGyro-mean()-X

30          425 fBodyGyro-mean()-Y

31          426 fBodyGyro-mean()-Z

32          503 fBodyAccMag-mean()

33  516 fBodyBodyAccJerkMag-mean()

34     529 fBodyBodyGyroMag-mean()

35 542 fBodyBodyGyroJerkMag-mean()

36              4 tBodyAcc-std()-X

37              5 tBodyAcc-std()-Y

38              6 tBodyAcc-std()-Z

39          44 tGravityAcc-std()-X

40          45 tGravityAcc-std()-Y

41          46 tGravityAcc-std()-Z

42         84 tBodyAccJerk-std()-X

43         85 tBodyAccJerk-std()-Y

44         86 tBodyAccJerk-std()-Z

45           124 tBodyGyro-std()-X

46           125 tBodyGyro-std()-Y

47           126 tBodyGyro-std()-Z

48       164 tBodyGyroJerk-std()-X

49       165 tBodyGyroJerk-std()-Y

50       166 tBodyGyroJerk-std()-Z

51           202 tBodyAccMag-std()

52        215 tGravityAccMag-std()

53       228 tBodyAccJerkMag-std()

54          241 tBodyGyroMag-std()

55      254 tBodyGyroJerkMag-std()

56            269 fBodyAcc-std()-X

57            270 fBodyAcc-std()-Y

58            271 fBodyAcc-std()-Z

59        348 fBodyAccJerk-std()-X

60        349 fBodyAccJerk-std()-Y

61        350 fBodyAccJerk-std()-Z

62           427 fBodyGyro-std()-X

63           428 fBodyGyro-std()-Y

64           429 fBodyGyro-std()-Z

65           504 fBodyAccMag-std()

66   517 fBodyBodyAccJerkMag-std()

67      530 fBodyBodyGyroMag-std()

68  543 fBodyBodyGyroJerkMag-std()



###Variable 1: 
$ subject                         (int) 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 4, 4, 4, ...
 
Number assigned of each volunteer (from 1 to 30)


###Variable 2:  
$ activity                        (fctr) LAYING, SITTING, STANDING, WALKING, WALKING_DOWNSTAIRS, WALKIN...

Each activity that the volunteers perform


###Variable 3, 4 and 5:  
$ 1 tBodyAcc-mean()-X             (dbl) 0.2215982, 0.2612376, 0.2789176, 0.2773308, 0.2891883, 0.255461...

$ 2 tBodyAcc-mean()-Y             (dbl) -0.040513953, -0.001308288, -0.016137590, -0.017383819, -0.0099...

$ 3 tBodyAcc-mean()-Z             (dbl) -0.11320355, -0.10454418, -0.11060182, -0.11114810, -0.10756619...

Body acceleration (mean): a variable for each axial: X, Y, Z 


###Variable 6, 7 and 8:  
$ 41 tGravityAcc-mean()-X         (dbl) -0.2488818, 0.8315099, 0.9429520, 0.9352232, 0.9318744, 0.89335...

$ 42 tGravityAcc-mean()-Y         (dbl) 0.70554977, 0.20441159, -0.27298383, -0.28216502, -0.26661034, ...

$ 43 tGravityAcc-mean()-Z         (dbl) 0.445817720, 0.332043703, 0.013490582, -0.068102864, -0.0621199...

Gravity acceleration (mean): a variable for each axial: X, Y, Z

###Variable 9, 10 and 11:  
$ 81 tBodyAccJerk-mean()-X        (dbl) 0.08108653, 0.07748252, 0.07537665, 0.07404163, 0.05415532, 0.1...

$ 82 tBodyAccJerk-mean()-Y        (dbl) 3.838204e-03, -6.191028e-04, 7.975731e-03, 2.827211e-02, 2.9650...

$ 83 tBodyAccJerk-mean()-Z        (dbl) 1.083424e-02, -3.367792e-03, -3.685250e-03, -4.168406e-03, -1.0...

Derived in time from body linear acceleration and angular velocity for each axial (mean): X, Y, Z

###Variable 12, 13 and 14:  
$ 121 tBodyGyro-mean()-X          (dbl) -0.016553094, -0.045350057, -0.023987735, -0.041830964, -0.0350...

$ 122 tBodyGyro-mean()-Y          (dbl) -0.064486124, -0.091924155, -0.059397221, -0.069530046, -0.0909...

$ 123 tBodyGyro-mean()-Z          (dbl) 0.14868944, 0.06293138, 0.07480075, 0.08494482, 0.09008501, 0.0...

Body giroscope measurement (mean) for each axial: X, Y, Z

###Variable 15, 16 and 17:  
$ 161 tBodyGyroJerk-mean()-X      (dbl) -0.10727095, -0.09367938, -0.09960921, -0.08999754, -0.07395920...

$ 162 tBodyGyroJerk-mean()-Y      (dbl) -0.04151729, -0.04021181, -0.04406279, -0.03984287, -0.04399028...

$ 163 tBodyGyroJerk-mean()-Z      (dbl) -0.07405012, -0.04670263, -0.04895055, -0.04613093, -0.02704611...

Derived in time from body giroscope measurement (mean) for each axial: X, Y, Z

###Variable 18:  
$ 201 tBodyAccMag-mean()          (dbl) -0.84192915, -0.94853679, -0.98427821, -0.13697118, 0.02718829,...

Magnitude of body acceleration calculated using the Euclidean norm (mean)

###Variable 19:
$ 214 tGravityAccMag-mean()       (dbl) -0.84192915, -0.94853679, -0.98427821, -0.13697118, 0.02718829,...

Magnitude of gravity acceleration calculated using the Euclidean norm (mean)

###Variable 20:
$ 227 tBodyAccJerkMag-mean()      (dbl) -0.954396265, -0.987364196, -0.992367791, -0.141428809, -0.0894...

Magnitude of body acceleration jerk calculated using the Euclidean norm (mean)

###Variable 21:  
$ 240 tBodyGyroMag-mean()         (dbl) -0.87475955, -0.93089249, -0.97649379, -0.16097955, -0.07574125...

Magnitude of body giroscope measurement calculated using the Euclidean norm (mean)

###Variable 22:
$ 253 tBodyGyroJerkMag-mean()     (dbl) -0.96346103, -0.99197634, -0.99496679, -0.29870368, -0.29546384...

Magnitude of body giroscope measurement jerk calculated using the Euclidean norm (mean)

###Variable 23, 24 and 25:
$ 266 fBodyAcc-mean()-X           (dbl) -0.93909905, -0.97964124, -0.99524993, -0.20279431, 0.03822918,...

$ 267 fBodyAcc-mean()-Y           (dbl) -0.867065205, -0.944084550, -0.977070848, 0.089712726, 0.001549...

$ 268 fBodyAcc-mean()-Z           (dbl) -0.8826669, -0.9591849, -0.9852971, -0.3315601, -0.2255745, -0....

Frequency domain signals from body accelerator (mean) for each axial: X, Y, Z

###Variable 26, 27 and 28:
$ 345 fBodyAccJerk-mean()-X       (dbl) -0.95707388, -0.98659702, -0.99463080, -0.17054696, -0.02766387...

$ 346 fBodyAccJerk-mean()-Y       (dbl) -0.92246261, -0.98157947, -0.98541870, -0.03522552, -0.12866716...

$ 347 fBodyAccJerk-mean()-Z       (dbl) -0.9480609, -0.9860531, -0.9907522, -0.4689992, -0.2883347, -0....

Frequency domain signals from body accelerator jerk (mean) for each axial: X, Y, Z

###Variable 29, 30 and 31:
$ 424 fBodyGyro-mean()-X          (dbl) -0.85024917, -0.97616146, -0.98638679, -0.33903220, -0.35244963...

$ 425 fBodyGyro-mean()-Y          (dbl) -0.95219149, -0.97583859, -0.98898446, -0.10305942, -0.05570225...

$ 426 fBodyGyro-mean()-Z          (dbl) -0.90930272, -0.95131554, -0.98077312, -0.25594094, -0.03186943...

Frequency domain signals from body giroscope measurement (mean) for each axial: X, Y, Z

###Variable 32:
$ 503 fBodyAccMag-mean()          (dbl) -0.86176765, -0.94778292, -0.98535636, -0.12862345, 0.09658453,...

Magnitude, of frequency domain signals, body giroscope acceleration jerk calculated using the Euclidean norm (mean)

###Variable 33:
$ 516 fBodyBodyAccJerkMag-mean()  (dbl) -0.933300361, -0.985262127, -0.992542478, -0.057119400, 0.02621...

Magnitude, of frequency domain signals, body acceleration jerk calculated using the Euclidean norm (mean)

###Variable 34:
$ 529 fBodyBodyGyroMag-mean()     (dbl) -0.86219019, -0.95843559, -0.98461762, -0.19925257, -0.18572029...

Magnitude, of frequency domain signals, body giroscope measurement calculated using the Euclidean norm (mean)

###Variable 35:
$ 542 fBodyBodyGyroJerkMag-mean() (dbl) -0.9423669, -0.9897975, -0.9948154, -0.3193086, -0.2819634, -0....

Magnitude, of frequency domain signals, body giroscope measurement jerk calculated using the Euclidean norm (mean)

###Variable 36, 37 and 38:
$ 4 tBodyAcc-std()-X              (dbl) -0.92805647, -0.97722901, -0.99575990, -0.28374026, 0.03003534,...

$ 5 tBodyAcc-std()-Y              (dbl) -0.836827406, -0.922618642, -0.973190056, 0.114461337, -0.03193...

$ 6 tBodyAcc-std()-Z              (dbl) -0.82606140, -0.93958629, -0.97977588, -0.26002790, -0.23043421...

Body acceleration (standar deviation): a variable for each axial: X, Y, Z 

###Variable 39, 40 and 41:
$ 44 tGravityAcc-std()-X          (dbl) -0.8968300, -0.9684571, -0.9937630, -0.9766096, -0.9505598, -0....

$ 45 tGravityAcc-std()-Y          (dbl) -0.9077200, -0.9355171, -0.9812260, -0.9713060, -0.9370187, -0....

$ 46 tGravityAcc-std()-Z          (dbl) -0.8523663, -0.9490409, -0.9763241, -0.9477172, -0.8959397, -0....

Gravity acceleration (standar deviation): a variable for each axial: X, Y, Z

###Variable 42, 43 and 44:
$ 84 tBodyAccJerk-std()-X         (dbl) -0.95848211, -0.98643071, -0.99460454, -0.11361560, -0.01228386...

$ 85 tBodyAccJerk-std()-Y         (dbl) -0.924149274, -0.981371965, -0.985648732, 0.067002501, -0.10160...

$ 86 tBodyAccJerk-std()-Z         (dbl) -0.9548551, -0.9879108, -0.9922512, -0.5026998, -0.3457350, -0....

Derived in time from body linear acceleration and angular velocity for each axial (standar deviation): X, Y, Z

###Variable 45, 46 and 47:
$ 124 tBodyGyro-std()-X           (dbl) -0.8735439, -0.9772113, -0.9871919, -0.4735355, -0.4580305, -0....

$ 125 tBodyGyro-std()-Y           (dbl) -0.951090440, -0.966473895, -0.987734440, -0.054607769, -0.1263...

$ 126 tBodyGyro-std()-Z           (dbl) -0.90828466, -0.94142592, -0.98064563, -0.34426663, -0.12470245...

Body giroscope measurement (standar deviation) for each axial: X, Y, Z

###Variable 48, 49 and 50:
$ 164 tBodyGyroJerk-std()-X       (dbl) -0.9186085, -0.9917316, -0.9929451, -0.2074219, -0.4870273, -0....

$ 165 tBodyGyroJerk-std()-Y       (dbl) -0.9679072, -0.9895181, -0.9951379, -0.3044685, -0.2388248, -0....

$ 166 tBodyGyroJerk-std()-Z       (dbl) -0.95779016, -0.98793581, -0.99210847, -0.40425545, -0.26876148...

Derived in time from body giroscope measurement (standar deviation) for each axial: X, Y, Z

###Variable 51:
$ 202 tBodyAccMag-std()           (dbl) -0.79514486, -0.92707842, -0.98194293, -0.21968865, 0.01988435,...

Magnitude, of frequency domain signals, body giroscope acceleration jerk calculated using the Euclidean norm (standar deviation)

###Variable 52:
$ 215 tGravityAccMag-std()        (dbl) -0.79514486, -0.92707842, -0.98194293, -0.21968865, 0.01988435,...

Magnitude of gravity acceleration calculated using the Euclidean norm (standar deviation)

###Variable 53:
$ 228 tBodyAccJerkMag-std()       (dbl) -0.92824563, -0.98412002, -0.99309621, -0.07447175, -0.02578772...

Magnitude of body acceleration jerk calculated using the Euclidean norm (standar deviation)

###Variable 54:
$ 241 tBodyGyroMag-std()          (dbl) -0.81901017, -0.93453184, -0.97869003, -0.18697836, -0.22572437...

Magnitude of body giroscope measurement calculated using the Euclidean norm (standar deviation)

###Variable 55:
$ 254 tBodyGyroJerkMag-std()      (dbl) -0.9358410, -0.9883087, -0.9947332, -0.3253249, -0.3065106, -0....

Magnitude of body giroscope measurement jerk calculated using the Euclidean norm (standar deviation)

###Variable 56, 57 and 58:
$ 269 fBodyAcc-std()-X            (dbl) -0.924437435, -0.976412313, -0.996028345, -0.319134720, 0.02433...

$ 270 fBodyAcc-std()-Y            (dbl) -0.833625556, -0.917275006, -0.972293102, 0.056040007, -0.11296...

$ 271 fBodyAcc-std()-Z            (dbl) -0.81289156, -0.93446956, -0.97793726, -0.27968675, -0.29792789...

Frequency domain signals from body accelerator for each axial (standar deviation): X, Y, Z

###Variable 59, 60 and 61:
$ 348 fBodyAccJerk-std()-X        (dbl) -0.96416071, -0.98749299, -0.99507376, -0.13358661, -0.08632790...

$ 349 fBodyAccJerk-std()-Y        (dbl) -0.932217870, -0.982513910, -0.987018227, 0.106739857, -0.13458...

$ 350 fBodyAccJerk-std()-Z        (dbl) -0.9605870, -0.9883392, -0.9923498, -0.5347134, -0.4017215, -0....

Frequency domain signals from body accelerator jerk (standar deviation) for each axial: X, Y, Z

###Variable 62, 63 and 64:
$ 427 fBodyGyro-std()-X           (dbl) -0.8822965, -0.9779042, -0.9874971, -0.5166919, -0.4954225, -0....

$ 428 fBodyGyro-std()-Y           (dbl) -0.95123205, -0.96234504, -0.98710773, -0.03350816, -0.18141473...

$ 429 fBodyGyro-std()-Z           (dbl) -0.9165825, -0.9439178, -0.9823453, -0.4365622, -0.2384436, -0....

Frequency domain signals from body giroscope measurement (standar deviation) for each axial: X, Y, Z

###Variable 65:
$ 504 fBodyAccMag-std()           (dbl) -0.79830094, -0.92844480, -0.98231380, -0.39803259, -0.18653030...

Magnitude, of frequency domain signals, body giroscope acceleration jerk calculated using the Euclidean norm (standar deviation)

###Variable 66:
$ 517 fBodyBodyAccJerkMag-std()   (dbl) -0.92180398, -0.98160618, -0.99253600, -0.10349240, -0.10405226...

Magnitude, of frequency domain signals, body acceleration jerk calculated using the Euclidean norm (standar deviation)

###Variable 67:
$ 530 fBodyBodyGyroMag-std()      (dbl) -0.8243194, -0.9321984, -0.9784661, -0.3210180, -0.3983504, -0....

Magnitude, of frequency domain signals, body giroscope measurement calculated using the Euclidean norm (standar deviation)

###Variable 68:
$ 543 fBodyBodyGyroJerkMag-std()  (dbl) -0.9326607, -0.9870496, -0.9946711, -0.3816019, -0.3919199, -0....

Magnitude, of frequency domain signals, body acceleration jerk calculated using the Euclidean norm (standar deviation)

### Notes on variable 3 to 68
The names of the variables are based on this points:
 - If the unit of the variable is time domain signals, they are captured at a constant rate of 50 Hz, filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. The prefix for this variables is "t"
 
 - A Fast Fourier Transform (FFT) has been applied to some of the signals: the results are stored in variables with the "f" prefix.
 
 - X, Y, Z has been used to denote 3-axial signals in the X, Y and Z directions.
 
 

##Sources
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

