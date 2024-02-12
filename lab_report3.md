# **Lab Report 3**

## Part 1 <br/>

-The bug that I will choose from week 4 is from the `ArrayExamples.java`. 

```
@Test
  public void testReversedFail() {
    int[] input1 = {1, 2, 3, 4, 5};
    assertArrayEquals(new int[]{5, 4, 3, 2, 1}, ArrayExamples.reversed(input1));
  }
```
```
@Test
  public void testReversedNoFail() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
- In the first JUnit test case, I created an input array that had the values 1, 2, 3, 4, 5 and expected an array of 5, 4, 3, 2, 1 when calling the `reversed` method on the input array. This is meant to be the failure-inducing input
- In the second JUnit test case, I used an input array that had no values with an expected array being an array with no values as calling `reversed` on the input array will yield in itself. 

![Image of Tests Being Ran](images/week5_1.png)
- Here we can see that the first JUnit failed, telling us that the expected, `5`, which was the first index of our expected array, was not what we received, `0`. This tells us that there is something wrong with the underlying method's code.
- The second JUnit test passed and seems to have passed since a reversed version of an array with no elements should be itself. 

Code before debugging: </br>
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
Code after debugging: </br>
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

To fix the code, I changed the fourth line of the `reversed` method to `newArray[i] = arr[arr.length - i - 1];` and the reason this fixes the bug is because 
the original code set all the elements of the input array to 0 and then returned the original array, which gave us the symptom earlier of `0` instead of `5`.
In the new version of the code, the input array is not changed but the newArray's element is set to the input arrays last index and increments down to the element at the first index. We then return the newArray. </br>

## Part 2 </br>
First, I decided I wanted to use the `less` command to talk about and to find out what options I should use of `less`, I went to ChatGPT and asked `Hi, can you provide me with 4 options I could use with the less command in the terminal`. The AI's response was ![ChatGPT output](images/week5_2.png) </br>

So in this image, ChatGPT provides us with the `less` options of `-N`, `-S`, `+F`, and `-i`. </br>

For the `-N` option, I decided to use the `biomed` directory in `technical` and chose two files to use `less -N` on.


```
aludoan@Andrew:~/cse15l_lab$ less -N docsearch/technical/biomed/bcr583.txt
      1
      2
      3
      4
      5         Introduction
      6         The evidence that adolescent diet may affect the risk of
      7         breast cancer derives from several lines of evidence [ 1 ]
      8         . Rates of breast cancer among Asian immigrants to the
      9         United States do not approach those of US white women until
     10         the second or third generation, suggesting that exposures
     11         during childhood and adolescence are important in
     12         establishing a higher risk of breast cancer [ 2 3 ] .
     13         Norwegian women who were adolescents during World War II,
     14         when average caloric intake decreased by 22%, have a
     15         reduced incidence of breast cancer, suggesting that energy
     16         restriction might affect risk [ 4 ] . Similarly, in animal
     17         models, energy restriction in the peripubertal period
     18         inhibits mammary tissue proliferation and reduces the
     19         subsequent risk of mammary tumors [ 5 6 ] . Exposure of
     20         rats to carcinogens before first pregnancy increases the
     21         incidence of mammary tumors compared with exposure after
     22         first pregnancy [ 7 ] . After differentiation of the
     23         mammary gland at the time of first full-term pregnancy of
     24         the rat, the rate of cell division decreases and length of
     25         the cell cycle increases, allowing more time for DNA repair
     26         [ 8 ] . This biologic phenomenon might explain the apparent
     27         vulnerability of the adolescent breast tissue to
     28         carcinogenic exposures. Among atomic bomb survivors and
     29         women exposed to ionizing radiation as part of their
     30         treatment for Hodgkin's disease, the risk of breast cancer
```
```
aludoan@Andrew:~/cse15l_lab$ less -N docsearch/technical/biomed/1472-6831-3-1.txt
      1
      2
      3
      4
      5         Background
      6         CADCAM technologies have found increased use in
      7         dentistry during the past 15 years. Cerec, a system
      8         invented by Mörmann and Brandistini [ 1 2 ] , was the first
      9         commercially available CADCAM system. Cerec was designed
     10         for making ceramic inlays and veneers, and these should be
     11         etched and bonded to the tooth with resin based luting
     12         agents [ 3 4 ] . Resin bonding was promoted because it
     13         improved retention and sealed gaps around Cerec
     14         restorations. Such gaps were often wider around the early
     15         Cerec restorations than they were around cast restorations.
     16         In addition, clinical experience evolving at that time
     17         suggested that the fracture rate of ceramic restorations
     18         decreased if they were resin bonded rather than cemented
     19         with traditional zinc phosphate or glass ionomer cements [
     20         5 ] . However, because of high equipment cost and a not yet
     21         optimised technology, the Cerec system did not capture a
     22         big market share. Instead, it was Procera, a system
     23         originally developed for industrial production of titanium
     24         crowns that become the CADCAM system of choice during the
     25         late 80 thand the early 90 th [ 6 7 ] . Procera did not
     26         become popular because of its titanium crowns but rather
     27         for its all-ceramic crowns [ 8 ] . These crowns consisted
     28         of Al
     29         2 O
     30         3 copings [ 8 ] with good fit and high
```
When using the `less -N` option on two separate files, `bcr583.txt` and `1472-6831-3-1.txt`, less displays the contents of the files one page at a time, but with the `-N` option, we also get the line numbers on the side which can be useful for remembering which line a certan phrase was said. 




