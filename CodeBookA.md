# Codebook for the Getting and Cleaning Data Project
The run_analysis.R code will read the 'Human Activity Recognition Using Smartphones Data Set' avaliable at https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

It will
- Merged both training and test sets (/test/X_test.txt and /train/X_train.txt).
- Includes the subjects who performed the activities from (/test/subject_train.txt and /train/subject_test.txt).
- Added Subject Id�s (1-30) 
- Extracted only mean or standard deviation measure (mean or std in feature name) from the original dataset.
- Does NOT include the Inertial Signals.
- It properly labels all the data.
- Added Activity names to all data
- Does not include data subset for 'angle' values
- It creates a tidy data set with average of the variables for each activity and for every subject.
- It exports the final tidy data set to a �UCI_TidyData.txt'.
- It exports the transformed clean data set to �UCI_CleanData.txt' .
- In the final file you will have a row for the average of each measured variable of the subset and each column represents a SUBJECT.ACTIVITY .

Tidy dataset have 180 rows and 68 columns

## str(data.tidy)

 - activities               : chr  "laying" "sitting" "standing" "walking" ...
 - subject                  : num  1 1 1 1 1 1 2 2 2 2 ...
 - tbodyacc-mean-x          : num  0.222 0.261 0.279 0.277 0.289 ...
 - tbodyacc-mean-y          : num  -0.04051 -0.00131 -0.01614 -0.01738 -0.00992 ...
 - tbodyacc-mean-z          : num  -0.113 -0.105 -0.111 -0.111 -0.108 ...
 - tbodyacc-std-x           : num  -0.928 -0.977 -0.996 -0.284 0.03 ...
 - tbodyacc-std-y           : num  -0.8368 -0.9226 -0.9732 0.1145 -0.0319 ...
 - tbodyacc-std-z           : num  -0.826 -0.94 -0.98 -0.26 -0.23 ...
 - tgravityacc-mean-x       : num  -0.249 0.832 0.943 0.935 0.932 ...
 - tgravityacc-mean-y       : num  0.706 0.204 -0.273 -0.282 -0.267 ...
 - tgravityacc-mean-z       : num  0.4458 0.332 0.0135 -0.0681 -0.0621 ...
 - tgravityacc-std-x        : num  -0.897 -0.968 -0.994 -0.977 -0.951 ...
 - tgravityacc-std-y        : num  -0.908 -0.936 -0.981 -0.971 -0.937 ...
 - tgravityacc-std-z        : num  -0.852 -0.949 -0.976 -0.948 -0.896 ...
 - tbodyaccjerk-mean-x      : num  0.0811 0.0775 0.0754 0.074 0.0542 ...
 - tbodyaccjerk-mean-y      : num  0.003838 -0.000619 0.007976 0.028272 0.02965 ...
 - tbodyaccjerk-mean-z      : num  0.01083 -0.00337 -0.00369 -0.00417 -0.01097 ...
 - tbodyaccjerk-std-x       : num  -0.9585 -0.9864 -0.9946 -0.1136 -0.0123 ...
 - tbodyaccjerk-std-y       : num  -0.924 -0.981 -0.986 0.067 -0.102 ...
 - tbodyaccjerk-std-z       : num  -0.955 -0.988 -0.992 -0.503 -0.346 ...
 - tbodygyro-mean-x         : num  -0.0166 -0.0454 -0.024 -0.0418 -0.0351 ...
 - tbodygyro-mean-y         : num  -0.0645 -0.0919 -0.0594 -0.0695 -0.0909 ...
 - tbodygyro-mean-z         : num  0.1487 0.0629 0.0748 0.0849 0.0901 ...
 - tbodygyro-std-x          : num  -0.874 -0.977 -0.987 -0.474 -0.458 ...
 - tbodygyro-std-y          : num  -0.9511 -0.9665 -0.9877 -0.0546 -0.1263 ...
 - tbodygyro-std-z          : num  -0.908 -0.941 -0.981 -0.344 -0.125 ...
 - tbodygyrojerk-mean-x     : num  -0.1073 -0.0937 -0.0996 -0.09 -0.074 ...
 - tbodygyrojerk-mean-y     : num  -0.0415 -0.0402 -0.0441 -0.0398 -0.044 ...
 - tbodygyrojerk-mean-z     : num  -0.0741 -0.0467 -0.049 -0.0461 -0.027 ...
 - tbodygyrojerk-std-x      : num  -0.919 -0.992 -0.993 -0.207 -0.487 ...
 - tbodygyrojerk-std-y      : num  -0.968 -0.99 -0.995 -0.304 -0.239 ...
 - tbodygyrojerk-std-z      : num  -0.958 -0.988 -0.992 -0.404 -0.269 ...
 - tbodyaccmag-mean         : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
 - tbodyaccmag-std          : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
 - tgravityaccmag-mean      : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
 - tgravityaccmag-std       : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
 - tbodyaccjerkmag-mean     : num  -0.9544 -0.9874 -0.9924 -0.1414 -0.0894 ...
 - tbodyaccjerkmag-std      : num  -0.9282 -0.9841 -0.9931 -0.0745 -0.0258 ...
 - tbodygyromag-mean        : num  -0.8748 -0.9309 -0.9765 -0.161 -0.0757 ...
 - tbodygyromag-std         : num  -0.819 -0.935 -0.979 -0.187 -0.226 ...
 - tbodygyrojerkmag-mean    : num  -0.963 -0.992 -0.995 -0.299 -0.295 ...
 - tbodygyrojerkmag-std     : num  -0.936 -0.988 -0.995 -0.325 -0.307 ...
 - fbodyacc-mean-x          : num  -0.9391 -0.9796 -0.9952 -0.2028 0.0382 ...
 - fbodyacc-mean-y          : num  -0.86707 -0.94408 -0.97707 0.08971 0.00155 ...
 - fbodyacc-mean-z          : num  -0.883 -0.959 -0.985 -0.332 -0.226 ...
 - fbodyacc-std-x           : num  -0.9244 -0.9764 -0.996 -0.3191 0.0243 ...
 - fbodyacc-std-y           : num  -0.834 -0.917 -0.972 0.056 -0.113 ...
 - fbodyacc-std-z           : num  -0.813 -0.934 -0.978 -0.28 -0.298 ...
 - fbodyaccjerk-mean-x      : num  -0.9571 -0.9866 -0.9946 -0.1705 -0.0277 ...
 - fbodyaccjerk-mean-y      : num  -0.9225 -0.9816 -0.9854 -0.0352 -0.1287 ...
 - fbodyaccjerk-mean-z      : num  -0.948 -0.986 -0.991 -0.469 -0.288 ...
 - fbodyaccjerk-std-x       : num  -0.9642 -0.9875 -0.9951 -0.1336 -0.0863 ...
 - fbodyaccjerk-std-y       : num  -0.932 -0.983 -0.987 0.107 -0.135 ...
 - fbodyaccjerk-std-z       : num  -0.961 -0.988 -0.992 -0.535 -0.402 ...
 - fbodygyro-mean-x         : num  -0.85 -0.976 -0.986 -0.339 -0.352 ...
 - fbodygyro-mean-y         : num  -0.9522 -0.9758 -0.989 -0.1031 -0.0557 ...
 - fbodygyro-mean-z         : num  -0.9093 -0.9513 -0.9808 -0.2559 -0.0319 ...
 - fbodygyro-std-x          : num  -0.882 -0.978 -0.987 -0.517 -0.495 ...
 - fbodygyro-std-y          : num  -0.9512 -0.9623 -0.9871 -0.0335 -0.1814 ...
 - fbodygyro-std-z          : num  -0.917 -0.944 -0.982 -0.437 -0.238 ...
 - fbodyaccmag-mean         : num  -0.8618 -0.9478 -0.9854 -0.1286 0.0966 ...
 - fbodyaccmag-std          : num  -0.798 -0.928 -0.982 -0.398 -0.187 ...
 - fbodybodyaccjerkmag-mean : num  -0.9333 -0.9853 -0.9925 -0.0571 0.0262 ...
 - fbodybodyaccjerkmag-std  : num  -0.922 -0.982 -0.993 -0.103 -0.104 ...
 - fbodybodygyromag-mean    : num  -0.862 -0.958 -0.985 -0.199 -0.186 ...
 - fbodybodygyromag-std     : num  -0.824 -0.932 -0.978 -0.321 -0.398 ...
 - fbodybodygyrojerkmag-mean: num  -0.942 -0.99 -0.995 -0.319 -0.282 ...
 - fbodybodygyrojerkmag-std : num  -0.933 -0.987 -0.995 -0.382 -0.392 ...

## Sample data from tidy dataset
### head(data.tidy)
          activities subject tbodyacc-mean-x tbodyacc-mean-y tbodyacc-mean-z tbodyacc-std-x tbodyacc-std-y
             laying       1       0.2215982    -0.040513953      -0.1132036    -0.92805647   -0.836827406
            sitting       1       0.2612376    -0.001308288      -0.1045442    -0.97722901   -0.922618642
           standing       1       0.2789176    -0.016137590      -0.1106018    -0.99575990   -0.973190056
            walking       1       0.2773308    -0.017383819      -0.1111481    -0.28374026    0.114461337
 walking_downstairs       1       0.2891883    -0.009918505      -0.1075662     0.03003534   -0.031935943
    walking_upstairs       1       0.2554617    -0.023953149      -0.0973020    -0.35470803   -0.002320265

 tbodyacc-std-z  tgravityacc-mean-x  tgravityacc-mean-y  tgravityacc-mean-z  tgravityacc-std-x  tgravityacc-std-y 
    -0.82606140         -0.2488818          0.7055498         0.44581772        -0.8968300        -0.9077200
    -0.93958629          0.8315099          0.2044116         0.33204370        -0.9684571        -0.9355171
    -0.97977588          0.9429520         -0.2729838         0.01349058        -0.9937630        -0.9812260
    -0.26002790          0.9352232         -0.2821650        -0.06810286        -0.9766096        -0.9713060
    -0.23043421          0.9318744         -0.2666103        -0.06211996        -0.9505598        -0.9370187
    -0.01947924          0.8933511         -0.3621534        -0.07540294        -0.9563670        -0.9528492
 
 tgravityacc-std-z tbodyaccjerk-mean-x tbodyaccjerk-mean-y tbodyaccjerk-mean-z tbodyaccjerk-std-x
        -0.8523663          0.08108653        0.0038382040         0.010834236        -0.95848211
        -0.9490409          0.07748252       -0.0006191028        -0.003367792        -0.98643071
        -0.9763241          0.07537665        0.0079757309        -0.003685250        -0.99460454
        -0.9477172          0.07404163        0.0282721096        -0.004168406        -0.11361560
        -0.8959397          0.05415532        0.0296504490        -0.010971973        -0.01228386
        -0.9123794          0.10137273        0.0194863076        -0.045562545        -0.44684389
		
 tbodyaccjerk-std-y tbodyaccjerk-std-z tbodygyro-mean-x tbodygyro-mean-y tbodygyro-mean-z tbodygyro-std-x
		 -0.9241493         -0.9548551      -0.01655309      -0.06448612       0.14868944      -0.8735439
         -0.9813720         -0.9879108      -0.04535006      -0.09192415       0.06293138      -0.9772113
         -0.9856487         -0.9922512      -0.02398773      -0.05939722       0.07480075      -0.9871919
          0.0670025         -0.5026998      -0.04183096      -0.06953005       0.08494482      -0.4735355
         -0.1016014         -0.3457350      -0.03507819      -0.09093713       0.09008501      -0.4580305
         -0.3782744         -0.7065935       0.05054938      -0.16617002       0.05835955      -0.5448711
 tbodygyro-std-y tbodygyro-std-z tbodygyrojerk-mean-x tbodygyrojerk-mean-y tbodygyrojerk-mean-z
    -0.951090440      -0.9082847          -0.10727095          -0.04151729          -0.07405012
    -0.966473895      -0.9414259          -0.09367938          -0.04021181          -0.04670263
    -0.987734440      -0.9806456          -0.09960921          -0.04406279          -0.04895055
    -0.054607769      -0.3442666          -0.08999754          -0.03984287          -0.04613093
    -0.126349195      -0.1247025          -0.07395920          -0.04399028          -0.02704611
     0.004105184      -0.5071687          -0.12223277          -0.04214859          -0.04071255
 tbodygyrojerk-std-x tbodygyrojerk-std-y tbodygyrojerk-std-z tbodyaccmag-mean tbodyaccmag-std tgravityaccmag-mean
          -0.9186085          -0.9679072          -0.9577902      -0.84192915     -0.79514486         -0.84192915
          -0.9917316          -0.9895181          -0.9879358      -0.94853679     -0.92707842         -0.94853679
          -0.9929451          -0.9951379          -0.9921085      -0.98427821     -0.98194293         -0.98427821
          -0.2074219          -0.3044685          -0.4042555      -0.13697118     -0.21968865         -0.13697118
          -0.4870273          -0.2388248          -0.2687615       0.02718829      0.01988435          0.02718829
          -0.6147865          -0.6016967          -0.6063320      -0.12992763     -0.32497093         -0.12992763
 tgravityaccmag-std tbodyaccjerkmag-mean tbodyaccjerkmag-std tbodygyromag-mean tbodygyromag-std
        -0.79514486          -0.95439626         -0.92824563       -0.87475955       -0.8190102
        -0.92707842          -0.98736420         -0.98412002       -0.93089249       -0.9345318
        -0.98194293          -0.99236779         -0.99309621       -0.97649379       -0.9786900
        -0.21968865          -0.14142881         -0.07447175       -0.16097955       -0.1869784
         0.01988435          -0.08944748         -0.02578772       -0.07574125       -0.2257244
        -0.32497093          -0.46650345         -0.47899162       -0.12673559       -0.1486193
 tbodygyrojerkmag-mean tbodygyrojerkmag-std fbodyacc-mean-x fbodyacc-mean-y fbodyacc-mean-z fbodyacc-std-x
            -0.9634610           -0.9358410     -0.93909905    -0.867065205      -0.8826669    -0.92443743
            -0.9919763           -0.9883087     -0.97964124    -0.944084550      -0.9591849    -0.97641231
            -0.9949668           -0.9947332     -0.99524993    -0.977070848      -0.9852971    -0.99602835
            -0.2987037           -0.3253249     -0.20279431     0.089712726      -0.3315601    -0.31913472
            -0.2954638           -0.3065106      0.03822918     0.001549908      -0.2255745     0.02433084
            -0.5948829           -0.6485530     -0.40432178    -0.190976721      -0.4333497    -0.33742819
 fbodyacc-std-y fbodyacc-std-z fbodyaccjerk-mean-x fbodyaccjerk-mean-y fbodyaccjerk-mean-z fbodyaccjerk-std-x
    -0.83362556    -0.81289156         -0.95707388         -0.92246261          -0.9480609         -0.9641607
    -0.91727501    -0.93446956         -0.98659702         -0.98157947          -0.9860531         -0.9874930
    -0.97229310    -0.97793726         -0.99463080         -0.98541870          -0.9907522         -0.9950738
     0.05604001    -0.27968675         -0.17054696         -0.03522552          -0.4689992         -0.1335866
    -0.11296374    -0.29792789         -0.02766387         -0.12866716          -0.2883347         -0.0863279
     0.02176951     0.08595655         -0.47987525         -0.41344459          -0.6854744         -0.4619070
 fbodyaccjerk-std-y fbodyaccjerk-std-z fbodygyro-mean-x fbodygyro-mean-y fbodygyro-mean-z fbodygyro-std-x
         -0.9322179         -0.9605870       -0.8502492      -0.95219149      -0.90930272      -0.8822965
         -0.9825139         -0.9883392       -0.9761615      -0.97583859      -0.95131554      -0.9779042
         -0.9870182         -0.9923498       -0.9863868      -0.98898446      -0.98077312      -0.9874971
          0.1067399         -0.5347134       -0.3390322      -0.10305942      -0.25594094      -0.5166919
         -0.1345800         -0.4017215       -0.3524496      -0.05570225      -0.03186943      -0.4954225
         -0.3817771         -0.7260402       -0.4926117      -0.31947461      -0.45359721      -0.5658925
 fbodygyro-std-y fbodygyro-std-z fbodyaccmag-mean fbodyaccmag-std fbodybodyaccjerkmag-mean
     -0.95123205      -0.9165825      -0.86176765      -0.7983009              -0.93330036
     -0.96234504      -0.9439178      -0.94778292      -0.9284448              -0.98526213
     -0.98710773      -0.9823453      -0.98535636      -0.9823138              -0.99254248
     -0.03350816      -0.4365622      -0.12862345      -0.3980326              -0.05711940
     -0.18141473      -0.2384436       0.09658453      -0.1865303               0.02621849
      0.15153891      -0.5717078      -0.35239594      -0.4162601              -0.44265216
 fbodybodyaccjerkmag-std fbodybodygyromag-mean fbodybodygyromag-std fbodybodygyrojerkmag-mean
              -0.9218040            -0.8621902           -0.8243194                -0.9423669
              -0.9816062            -0.9584356           -0.9321984                -0.9897975
              -0.9925360            -0.9846176           -0.9784661                -0.9948154
              -0.1034924            -0.1992526           -0.3210180                -0.3193086
              -0.1040523            -0.1857203           -0.3983504                -0.2819634
              -0.5330599            -0.3259615           -0.1829855                -0.6346651
 fbodybodygyrojerkmag-std
               -0.9326607
               -0.9870496
               -0.9946711
               -0.3816019
               -0.3919199
               -0.6939305

Tidy dataset has mean of all the values of the 30 subjects in the given 6 activity levels. So it makes a total of 180 rows and 68 different measures.