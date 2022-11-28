## Grade.sh Script

# Code
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
    exit
fi

set +e

javac -cp $CPATH *.java
if [[ $? -eq 0 ]]
then
    echo "Compile Sucess! Grade +1"
else
    echo "Compile Failed, Grade: 1/4"
    exit
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

# Grading three student submissions
* https://github.com/ucsd-cse15l-f22/list-methods-corrected
<img width="727" alt="Screen Shot 2022-11-27 at 4 11 39 PM" src="https://user-images.githubusercontent.com/78475359/204167481-94290165-a04a-49fc-b595-411a072bf32b.png">

* https://github.com/ucsd-cse15l-f22/list-methods-compile-error
<img width="737" alt="Screen Shot 2022-11-27 at 4 12 57 PM" src="https://user-images.githubusercontent.com/78475359/204167557-4de8ab6e-b43f-4106-a74d-e8f8edd0484a.png">

* https://github.com/ucsd-cse15l-f22/list-methods-filename
<img width="732" alt="Screen Shot 2022-11-27 at 4 13 36 PM" src="https://user-images.githubusercontent.com/78475359/204167583-34709251-b32e-4686-9540-9979746492c6.png">




