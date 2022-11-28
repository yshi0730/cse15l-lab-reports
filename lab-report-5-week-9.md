# Grade.sh Script

## Code
```
set -e

rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission
cd student-submission
CPATH=.:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar

if [[ -e ListExamples.java ]]
then
    echo "Correct file found, Grade +1"
else 
    echo "File not found, Grade: 0/4"
    exit 1
fi

set +e

javac -cp $CPATH *.java
if [[ $? -eq 0 ]]
then
    echo "Compile Sucess! Grade +1"
else
    echo "Compile Failed, Grade: 1/4"
    exit 2
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > results.txt 
if [[ $? -eq 0 ]]
then
    echo "All Tests Passed! Grade + 2"
    echo "Final grade: 4/4"
    exit
else
    FAILURE=$(grep "There " results.txt | grep -Eo "[1-3]")
    PASSED="$((3 - $FAILURE))"
    echo "Tests Error!"
    echo "Final grade: $PASSED/4"
    cat results.txt
    exit 3
fi
```

## Grading three student submissions
* https://github.com/ucsd-cse15l-f22/list-methods-corrected
<img width="727" alt="Screen Shot 2022-11-27 at 4 11 39 PM" src="https://user-images.githubusercontent.com/78475359/204167481-94290165-a04a-49fc-b595-411a072bf32b.png">

* https://github.com/ucsd-cse15l-f22/list-methods-compile-error
<img width="737" alt="Screen Shot 2022-11-27 at 4 12 57 PM" src="https://user-images.githubusercontent.com/78475359/204167557-4de8ab6e-b43f-4106-a74d-e8f8edd0484a.png">

* https://github.com/ucsd-cse15l-f22/list-methods-filename
<img width="732" alt="Screen Shot 2022-11-27 at 4 13 36 PM" src="https://user-images.githubusercontent.com/78475359/204167583-34709251-b32e-4686-9540-9979746492c6.png">

## Trace of grade.sh with one submission example
* https://github.com/ucsd-cse15l-f22/list-methods-filename
```
set -e

rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission
cd student-submission
CPATH=.:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar
```
These lines remove any previous files in student-submission folder so that we can clone a new student submission and test it. Then it copies the TestListExamples.java into that folder for later test. Then we cd into the student-submission folder. CPATH is for later more convenient use of the java path. These lines have empty standard output and error. Their return code will be 0.

```
if [[ -e ListExamples.java ]]
then
    echo "Correct file found, Grade +1"
else 
    echo "File not found, Grade: 0/4"
    exit 1
fi
```
It first looks for ListExamples.java, the correct file to be there. If it finds it, we give the submission 1/4. Else, we give the submission 0/4 and exit the script.

For the example we are evaluating, it only contains a file named ListMethods.java, which is incorrect, so the scripts cannot find ListExamples.java. It won't run the then statement and it triggers the else statement. It receives 0/4 and the script exits. Standard output will be "File not found, Grade: 0/4", the only echo statement inside the else statement. It has no standard error. The return code for the echo statement is 0. Then the script exits successfully with code 1 indicating the student submission did not go through every steps. All lines of code after will not run since the script has terminated.
