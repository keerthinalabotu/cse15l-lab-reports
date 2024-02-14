## CSE 15L Lab 3
# Part 1

**Bugs**

A failure-inducing input for the buggy program, as a JUnit test and any associated code:

One of the errors is where the loop for the reversing of the Array in place has the wrong limit (JUnit test is below):
```
@Test
  public void testReverse(){
    int[] input2 = {1,3,4,5};
    ArrayExamples.reverseInPlace(input2);
    
    //System.out.println(input2);
    for (int i=0; i<input2.length-1; i++){
      System.out.println(input2[i]);
    }
    assertArrayEquals(new int[]{5,4,3,1}, input2);
  }
```

The test above should ideally return `{5,4,3,2,1}` but instead returns `5,4,4,5` due to an error within the limits. 

A test that does works is the following since the values in the array are the same:
```
@Test
  public void testReverse2(){
    int[] input2 = {1,1};
    ArrayExamples.reverseInPlace(input2);
    
    //System.out.println(input2);
    for (int i=0; i<input2.length-1; i++){
      System.out.println(input2[i]);
    }
    assertArrayEquals(new int[]{1,1}, input2);
  }
```

The test above should ideally return `1,1` and it does return that even though the code isn't necessarily correct since the reverse is the same if the values are the same in the array.

Screenshot of how the test doesn't work when we try to reverse the array `{1,2,3,4,5}`:

<img width="586" alt="reverse_fail" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/3ffec30d-1e46-4118-91dc-5a38e5b7f041">

Screenshot of how the test where we try to reverse `{1,1}` does work: 

<img width="534" alt="reverse_work" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/6841342b-1a8a-4ee7-aa1b-814c4bcaf2b0">

The bug before I fixed the code (the limit of the loop):

```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After I fixed the code:

```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    //int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length/2; i += 1) {
      int curr = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length-i-1]=curr;
    }
    //arr = newArray;
  }
```

The change I made was changing the end of the for loop from `arr.length` to `arr.length/2` since when we reverse we're changing both the beginning and the end at the same time anyway so if we go all the way to `arr.length` we end up reversing the changes that we made in the first place. 

Another change I made was creating a temporary placeholder `int curr=arr[i]` where it saves the current value that we end up changing and I used that to reset the value towards the end of the array. I also added a line where we reset the other side of the array along with the beginning. It was `arr[i]=arr[arr.length-i-1];`.

# Part 2

**Research Commands**

The command that I am using for part 2 is `grep`. Four alternate ways to use `grep` are `grep -w`, `grep -i`, `grep -v`, and `grep -r`. 

**First Command**

The first alternative way is `grep -w` which basically tries to find the input string that we put into the command line
within the file that we pass in. It looks for the whole word within the files (not as a sub-string).

The first example of using `grep -w`: 

```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -w "cvm" find-results.txt
```

The output of using that search within the `find-results.txt` was the following:

```
technical/biomed/cvm-2-1-038.txt
technical/biomed/cvm-2-4-180.txt
technical/biomed/cvm-2-4-187.txt
technical/biomed/cvm-2-6-278.txt
technical/biomed/cvm-2-6-286.txt
```

In this example our command uses `grep -w` for `"cvm"` which looks through the entire text file of `find-results.txt` 
and returns all the file names that contain the `String` that we are looking for which is `"cvm"` in this case. 
If the input `String` is not contained in the file it would return nothing. 

The second example of using `grep-w`: 
```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -w "gb-2000" find-results.txt
```

The output of using that search within the `find-results.txt` was the following:
```
technical/biomed/gb-2000-1-1-research002.txt
technical/biomed/gb-2000-1-2-research0003.txt
```

In this example our command uses `grep -w` for `"gb-2000"` through the entire file of `find-results.txt` to eventually
find two files containing the respective `String` that we passed in.

Sources: 
The source I used to find the functionality of `grep -w` was this:
https://www.educative.io/answers/what-is-the-grep-command-in-linux#:~:text=grep%20%2Dw%20%E2%80%9Cpattern%E2%80%9D%20file.&text=The%20%2Dw%20flag%20is%20used,not%20as%20a%20sub%2Dstring.

**Second Command**

The second alternative way is `grep -i` which tries to find the passed in `String` without taking account for any differences in capitalization differences. So for example if we were looking for the `String` "set" within a file it would return the name of the file even if it included "SEt" rather than "set".

The first example of using `grep -i`:

```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -i "GB-2000" find-results.txt
```

The output of using that command was the following: 

```
technical/biomed/gb-2000-1-1-research002.txt
technical/biomed/gb-2000-1-2-research0003.txt
```

In this example our command uses `grep -i` for `"GB-2000"` which looks through the entire text file of `find-results.txt` 
and returns all the file names that contain the `String` that we are looking for which is `"GB-2000"` in this case. Unlike `grep -w` however, it does not pay attention to capitalization differences and will return the file even if it contains `Gb-2000` or `gb-2000` or `gB-2000` instead of the requested `GB-2000`.

The second example of using `grep -i`: 

```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -i "CVM" find-results.txt
```

The output of the command above is the following: 

```
technical/biomed/cvm-2-1-038.txt
technical/biomed/cvm-2-4-180.txt
technical/biomed/cvm-2-4-187.txt
technical/biomed/cvm-2-6-278.txt
technical/biomed/cvm-2-6-286.txt
```

In this example, similar to our previous example, our command uses `grep -i` for `"CVM"` which looks through the entire text file of `find-results.txt` and returns all the file names that contain the `String` that we are looking for which is `"CVM"` in this case. Unlike `grep -w` however, it does not pay attention to capitalization differences and will return the file even if it contains `cVM` or `CvM` or `cvm` instead of the requested `CVM`.

Sources: 
The source I used to find the functionality of `grep -i` was this:
https://docs.rackspace.com/docs/use-the-linux-grep-command

**Third Command**

The third alternative way is `grep -v` which tries to find all the files that don't contain the passed in `String` and returns those files that don't contain the passed in `String`.

The first example of using `grep -v`:
```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -v "txt" find-results.txt
```
The command I used above tries to search within all the files in `find-results.txt` to find any file that doesn't contain `txt` within the file name. The output of that is below:

```
technical/biomed
```
In this example we use `grep -v` to search within all of our files in `find-results.txt` to find files that don't contain the String `txt` which is only one file that is eventually returned.

The second example of using `grep -v` is the following:

```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -v "biomed" biomed-sizes.txt
```

The result of the command above was the following: 

```
  490673  3437230 26818944 total
```
In this example we use `grep -v` to search within all of our files in `biomed-sizes.txt` to find files that don't contain the String ``biomed` which is only one file at the end containing all the total sizes that is eventually returned.

Sources: 
The source I used to find the functionality of `grep -v` was this: https://ioflood.com/blog/grep-exclude-how-to-use-v-to-exclude-words-patterns-or-files-in-grep/#:~:text=You%20use%20the%20'%2Dv',contain%20the%20pattern%20'exclude_this'.&text=By%20excluding%20certain%20patterns%2C%20you,streamline%20your%20data%20searching%20process.

**Fourth Command**

The third alternative way is `grep -r` which tries to find all the files that contain the `String` that we pass into the command within the file passed in, and returns the names of the files that contain the `String`. However, this is recursive meaning that no matter how nested the files are it will look within to find the desired `String`.

The first example of using `grep -r`:
```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -r "cvm" find-results.txt
```

The output of the command above: 

```
technical/biomed/cvm-2-1-038.txt
technical/biomed/cvm-2-4-180.txt
technical/biomed/cvm-2-4-187.txt
technical/biomed/cvm-2-6-278.txt
technical/biomed/cvm-2-6-286.txt
```

In this example our command uses `grep -r` for `"cvm"` which looks through the entire text file of `find-results.txt` 
and returns all the file names that contain the `String` that we are looking for which is `"cvm"` in this case. 
If the input `String` is not contained in the file it would return nothing. This seems very similar to `grep -w` since there are no subdirectories in this case, however, in general, it would return even more files if they existed within subdirectories. 

The second example of using `grep -r`: 
```
keert@keerthi-n MINGW64 ~/docsearch (main)
$ grep -r "gb-2000" find-results.txt
```

The output of the command above: 
```
technical/biomed/gb-2000-1-1-research002.txt
technical/biomed/gb-2000-1-2-research0003.txt
```

In this example our command uses `grep -r` for `"gb-2000"` which looks through the entire text file of `find-results.txt` 
and returns all the file names that contain the `String` that we are looking for which is `"gb-2000"` in this case. 
If the input `String` is not contained in the file it would return nothing. This seems very similar to `grep -w` since there are no subdirectories in this case, however, in general, it would return even more files if they existed within subdirectories. 

Sources:
I got my information about the functionality of `grep -r` from the following source: https://www.educative.io/answers/what-is-the-grep-function-in-r#:~:text=The%20grep()%20function%20in%20R%20is%20used%20to%20check,characters%20in%20a%20given%20string.
