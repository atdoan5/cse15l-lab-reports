# **Lab Report 3**

## Part 1 <br/>

-The bug that I will choose from week 4 is from the `ArrayExamples.java`. 

`
@Test
  public void testReversedFail() {
    int[] input1 = {1, 2, 3, 4, 5};
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, ArrayExamples.reversed(input1));
  }
`
`
@Test
  public void testReversedNoFail() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
'
- In the first JUnit test case, I created an input array that had the values 1, 2, 3, 4, 5 and expected an array of 5, 4, 3, 2, 1 when calling the `reversed` method on the input array. This is meant to be the failure-inducing input
- In the second JUnit test case, I used an input array that had no values with an expected array being an array with no values as calling `reversed` on the input array will yield in itself. 

![Image of Tests Being Ran](images/week5_1)
- Here we can see that the first JUnit failed, telling us that the expected, `5`, which was the first index of our expected array, was not what we received, `0`. This tells us that there is something wrong with the underlying method's code.
- The second JUnit test passed and seems to have passed since a reversed version of an array with no elements should be itself. 

Code before debugging: 
`
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
`
Code after debugging:
`
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
`
To fix the code, I changed the fourth line of the `reversed` method to `newArray[i] = arr[arr.length - i - 1];` and the reason this fixes the bug is because 
the original code set all the elements of the input array to 0 and then returned the original array, which gave us the symptom earlier of `0` instead of `5`.
In the new version of the code, the input array is not changed but the newArray's element is set to the input arrays last index and increments down to the element at the first index. We then return the newArray. </br>

## Part 2 </br>


