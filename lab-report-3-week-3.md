# Part1

1. Code of Simple SearchEngine

```
class Handler implements URLHandler {

    ArrayList<String> strings = new ArrayList<>();
    

    public String handleRequest(URI url) {
        
        if (url.getPath().contains("add")){
            String[] parameters = url.getQuery().split("=");
            strings.add(parameters[1]);
            String msg = String.format("String added: %s", parameters[1]);
            return msg;
            
        }
        else if (url.getPath().contains("search")){
            String[] parameters = url.getQuery().split("=");
            String searchItem = parameters[1];

            String toReturn = "";
            for(String string: strings){
                if(string.contains(searchItem)){
                    toReturn += string;
                    toReturn += ";";
                }
            }
            return toReturn;    
        }
        else{
            return "404 Not Found!";
        }
    }
}
```
2. Screenshots

<img width="357" alt="Screen Shot 2022-10-13 at 4 01 48 PM" src="https://user-images.githubusercontent.com/78475359/195726007-b3efc81d-8513-4f84-8f78-ffd5c2c6f3b5.png">
<img width="361" alt="Screen Shot 2022-10-13 at 4 02 29 PM" src="https://user-images.githubusercontent.com/78475359/195726083-70624c16-e589-4b58-bf28-9bc4206bdb41.png">
<img width="341" alt="Screen Shot 2022-10-13 at 4 02 46 PM" src="https://user-images.githubusercontent.com/78475359/195726106-5f2f677b-b38f-4332-8ae8-0072e7b6d760.png">

All of them called handleRequest method. The first two "add" called the first if statement
```
if (url.getPath().contains("add")){
            String[] parameters = url.getQuery().split("=");
            strings.add(parameters[1]);
            String msg = String.format("String added %s!", parameters[1]);
            return msg;
            
        }
```
which adds the string to the ArrayList for storing strings.
The "search" called the "else if" statement, which loops through the ArrayList and finds all strings that contains the string searched. I created a new empty string and add all matched strings to the empty string, each of which is separated by a semicolon. 

3. 



# Part 2

## ArrayExample 

1. Reverse() Method

- Test

```
@Test
  public void testReverse(){
    int[] input1 = {1,2,3,4,7,4,2};
    int[] expected = {2,4,7,4,3,2,1};
    assertArrayEquals(expected, ArrayExamples.reversed(input1));
  }
```

- Symptom 
<img width="742" alt="Screen Shot 2022-10-12 at 6 20 56 PM" src="https://user-images.githubusercontent.com/78475359/195477082-4df0ce32-cc05-471f-99ed-6df77b458d41.png">

- The bug and fix

The buggy code is commented out, replaced by functioning code:

```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {

      // arr[i] = newArray[arr.length - i - 1]; 
      newArray[i] = arr[arr.length - i - 1];
      
    }
    
    //return arr;
    return newArray;
```

- Connection between the bug and the symptom:

The buggy code wants to create new int[] newArray to store the elements of the original int[] arr in reverse order; but, in the for loop, it sets the i th element of the original array to be the (length of arr- i - 1)th element of newArray, which is clearly faulty because newArray does not contain any element at this point. 

Therefore, when my input is {1,2,3,4,7,4,2}, with the bug, the first element of the returned array is not 2 as expected. 



2. ReverseInPlace() Method
- Test
```
@Test
  public void testreverseInPlace(){
    int[] input1 = {1,2,3,4,7,4,2};
    int[] expected = {2,4,7,4,3,2,1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(expected, input1);
  }
```
- Symptom
<img width="745" alt="Screen Shot 2022-10-12 at 6 36 52 PM" src="https://user-images.githubusercontent.com/78475359/195478627-b7bf491b-9eda-4bb8-a1cf-0be232c79647.png">

- Bug and Fix

The bug is that it replaces the i th element by the length-i-1 th element; after reaching the mid point of the array, it continues to iterate and incorrectly changing the array. To fix it, I create a new int array to store the reversed elements, and changing arr accordingly in another for loop.
```
static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for(int i = 0; i < arr.length; i++){
      arr[i] = newArray[i];
    }
  }
```

- Connection between the bug and symptom

With the bug, after the iteration reaches the mid point, when it tries to change the i th element to the length-1-i th element, it ends up keeping the element. For example, an original array of {1,3,5,7,9} will be changed to {9,7,5,7,9} with the bug.

## 

