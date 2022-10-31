# Lab 4

## 3 Cool ways to use Find commands

Here are 3 ways you can use the find command

1. `-type f` and `-type d`

You can use `-type f` to find either a file or `-type d` to find only directories, which can be helpful if you only want to look for files or only look for directories.

### Command

```
find ./ -type d
```

### Output

```
./
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```

### Command
```
find ./ -type f -name "A*"
```

### Output

```
./government/Media/AP_LawSchoolDebts.txt
./government/Media/A_Perk_of_Age.txt
./government/Media/A_helping_hand.txt
./government/Media/Abuse_penalties.txt
./government/Media/Advocate_for_Poor.txt
./government/Media/Aid_Gets_7_Million.txt
./government/Media/All_May_Have_Justice.txt
./government/Media/Annual_Fee.txt
./government/Media/Anthem_Payout.txt
./government/Media/Assuring_Underprivileged.txt
./government/Media/Attorney_gives_his_time.txt
./government/Media/Avoids_Budget_Cut.txt
```

### Command
```
find ./ -type d -name "A*"
```

### Output
```
./government/About_LSC
./government/Alcohol_Problems
```

2. `-iname`

You can use `-iname` rather than `-name` because `-iname` isn't case-sensitive. This is useful because you won't have to type the find command multiple times to account for uppercase and lowercase letters

### Command
 ```
find ./ -type f -iname "A*"
 ```

 ### Output
 ```
./biomed/ar104.txt
./biomed/ar118.txt
./biomed/ar120.txt
./biomed/ar130.txt
./biomed/ar140.txt
./biomed/ar149.txt
./biomed/ar297.txt
./biomed/ar309.txt
./biomed/ar319.txt
./biomed/ar321.txt
./biomed/ar328.txt
./biomed/ar331.txt
./biomed/ar383.txt
./biomed/ar387.txt
./biomed/ar407.txt
./biomed/ar408.txt
./biomed/ar409.txt
./biomed/ar422.txt
./biomed/ar429.txt
./biomed/ar430.txt
./biomed/ar601.txt
./biomed/ar612.txt
./biomed/ar615.txt
./biomed/ar619.txt
./biomed/ar624.txt
./biomed/ar68.txt
./biomed/ar745.txt
./biomed/ar750.txt
./biomed/ar774.txt
./biomed/ar778.txt
./biomed/ar79.txt
./biomed/ar792.txt
./biomed/ar795.txt
./biomed/ar799.txt
./biomed/ar93.txt
./government/Env_Prot_Agen/atx1-6.txt
./government/Gen_Account_Office/ai00134.txt
./government/Gen_Account_Office/ai2132.txt
./government/Gen_Account_Office/ai9868.txt
./government/Media/AP_LawSchoolDebts.txt
./government/Media/A_Perk_of_Age.txt
./government/Media/A_helping_hand.txt
./government/Media/Abuse_penalties.txt
./government/Media/Advocate_for_Poor.txt
./government/Media/Aid_Gets_7_Million.txt
./government/Media/All_May_Have_Justice.txt
./government/Media/Annual_Fee.txt
./government/Media/Anthem_Payout.txt
./government/Media/Assuring_Underprivileged.txt
./government/Media/Attorney_gives_his_time.txt
./government/Media/Avoids_Budget_Cut.txt
./government/Media/agency_expands.txt
 ```

 ### Command
 ```
 find ./ -type d -iname "a*"
 ```

 ### Output
 ```
./government/About_LSC
./government/Alcohol_Problems
 ```

 ### Command
 ```
find -iname "Re*"
 ```

 ### Output
```
./government/About_LSC/reporting_system.txt
./government/Media/Rental_rules.txt
./government/Media/Retirement_Has_Its_Appeal.txt
./government/Media/residents_sue_city.txt
./government/Post_Rate_Comm/Redacted_Study.txt
./government/Post_Rate_Comm/ReportToCongress2002WEB.txt
```

3. `-size`

You can use `-size [file size]` to look forwad files of a certain size. 

For [file size], you type a number plus:

* c = bytes
* k = kilobytes
* M = megabytes
* G = gigabytes

You can also add:

* + = greater than this size
* - = less than this size

This is helpful if you are looking for large files/directories or small files/directories

### Command
```
find -size 10k
```

### Output

```
./911report/preface.txt
./biomed/1472-6769-1-4.txt
./government/Gen_Account_Office/og96014.txt
./government/Gen_Account_Office/og96023.txt
./government/Gen_Account_Office/og96040.txt
./government/Gen_Account_Office/og96047.txt
./government/Gen_Account_Office/og97039.txt
./government/Gen_Account_Office/og97051.txt
./government/Gen_Account_Office/og97052.txt
./government/Media/Farm_workers.txt
./plos/journal.pbio.0020042.txt
./plos/journal.pbio.0020073.txt
./plos/journal.pbio.0020156.txt
./plos/journal.pbio.0020215.txt
./plos/journal.pbio.0020224.txt
./plos/journal.pbio.0020297.txt
./plos/journal.pbio.0030131.txt
./plos/pmed.0020005.txt
./plos/pmed.0020075.txt
```

### Command
```
find -type d -size +10k
```

### Output
```
./biomed
./government/Media
./plos
```

### Command
```
find -size -2k
```

### Output
```
./plos/pmed.0020191.txt
./plos/pmed.0020226.txt
```