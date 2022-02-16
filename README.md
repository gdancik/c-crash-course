# c-crash-course

## Useful links
- Linux tutorial: https://gdancik.github.io/CSC-343/data/notes/linuxtut/index.html
- C Tutorial: https://www.tutorialspoint.com/cprogramming/index.htm
- Online C compiler: https://www.onlinegdb.com/online_c_compiler

## C examples

### Printing

```
#include <stdio.h>
  
int main () {

  printf("Hello World!\n");

  int num = 4;
  printf("The number is %d\n", num);

  double pi = 3.14;
  printf("pi is approximately %f\n", pi);

  // There are no string objects, only character arrays (more on this later)
  char school[] = "Eastern";
  printf("You are at %s\n", school);

  char name[] = "Jamie";
  int age = 24;
  printf("%s is %d years old\n", name, age);
  
  return 0;
}
```

###

### Statically declared arrays

An array that is *statically* declared has a fixed size at compile time and its size cannot be altered. You can specify the array size by specifying a constant size or by declaring and initializing the array in a single statement.

```
#include <stdio.h>

int main()
{
    
  int mynums[2] = {1,2}; // an integer array of size 2
  int morenums[] = {3,4,5}; // an integer array with size of 3 (size determined by initialization)

  const int n = 2;
  int evenmore[n];  // an integer array of size 2 (only works if size is constant)
  evenmore[0] = 90;
  evenmore[1] = 91;

  printf("mynums:\n");  
  printf("-----------\n");  
  for (int i = 0; i < 2; i++) {
      printf("Number at index %d is %d\n", i, mynums[i]);
  }

  printf("\n\n");
  
  printf("morenums:\n");  
  printf("-----------\n");  
  for (int i = 0; i < 2; i++) {
     printf("Number at index %d is %d\n", i, morenums[i]);
  }

  
  printf("\n\n");

  printf("evenmore:\n");  
  printf("-----------\n");  
  for (int i = 0; i < 2; i++) {
      printf("Number at index %d is %d\n", i, evenmore[i]);
  }

  return 0;
  
}
```

### Caution: no index out of bounds 

C will let you access elements outside the bounds of an array, though this can lead to a segmentation fault (when the program attempts to access memory that it is not allowed to access). Note: a compiler *may* give a warning but it will not prevent you from running your code.

```
#include <stdio.h>

int main()
{
    
  int numbers[] = {1,2,3};
  
  // this is valid
  printf("The first number is: %d\n", numbers[0]);
  
  // this will output a garbage value or can lead to a segmentation fault
  printf("A value outside the bounds of the array is: %d\n", numbers[9]);  

  return 0;
}
```

### Character arrays

Character arrays should end with a null terminator ('\0') to mark the end of a string. If not included, functions that use character arrays, such as *printf* and *strcpy*, will include characters passed the intended end of the string.

```
#include <stdio.h>
#include <string.h>

int main() {

  // correct approach -- null terminator is automatically added
  char word1[] = "word1";
  char word2[] = "word2";

  printf("word1: %s\nword2: %s\n\n", word1, word2);
  
  
  // incorrect -- there is no null terminator to mark the end of the string
  char word3[5] = "word3";
  char word4[5] = "word4";
  printf("word3: %s\nword4: %s\n\n", word3, word4);
  
  // correct approach - the size accounts for the null terminator
  char word5[6] = "word3";
  char word6[6] = "word4";
  printf("word5: %s\nword6: %s\n\n", word5, word6);
  
  // you can add a null terminator ('\0') to a character array
  printf("word3 without null terminator: %s\n", word3);
  
  word3[4] = '\0'; // add null terminator to end of "word"
  printf("word3 with null terminator added: %s\n\n", word3);
  
  return 0;
}
```
