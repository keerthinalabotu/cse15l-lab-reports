## CSE 15L Lab 4

**Student Question:**

Hello,

My implementation for Rotating an array list is not working when I run my bash grade.sh. I believe it might have something to do with how I'm accessing values within the copy array and assign them to the values array. 

The errors I received when running the bash grade.sh was this: 
![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/4ae615d0-2eb0-4f8a-b3d5-55584b596f86)

This might be since I pass in the value "i" within this code but it might go out of bounds when the value of "i" should be added with index and that might be out of bounds as well. 

The test cases that caused the errors were the following: 
![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/d1cb69a4-1e8a-488f-9e96-b0fcc6960027)

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e3f5d880-0f12-43c5-bc2d-6beb1c6b32e4)

I'm not too sure what is causing my error or if I have the correct assumption of what my error is. 

For reference, this is my code for my rotate method: 

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/76dcf30f-35a6-4a85-a7f3-89544739c7bf)

Thank you for your time!

_____________________________________________________________________________________

**TA response:**

Hi!

Your code looks really good so far! Something you might want to keep in mind is that for your second if loop you're not necessarily changing anything since you are passing in "i" for the index of copy that you are putting into values. But, notice that in your previous if loop you had just copied that over to your copy array. 

After you fix that index with what you really want to update values with, something else to keep in mind is that you might get an index out of bounds error so you may have to figure out a way to solve that (hint: you can use "mod" to try and solve the index out of bounds).

Hopefully this helps a bit!

-TA
__________________________________________________________________________________________

Information that student got from trying this:

The student probably understood from this that the value that they pass into the copy[] for the second if loop is never updated with the "index" that they are supposed to add. They also don't take into account the index out of bounds which they will eventually see as a problem when they see their terminal output.

After making a change to their code:

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/b4f5f2bf-0ba6-4d5b-812e-005db231d212)

Terminal output:

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e56ec222-d56c-4f25-ba5d-2f18a332a04c)

________________________________________________________________________

**Information needed about setup:**

The file & directory structure needed

- The file structure needed looks like this:
![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/153b7fa4-1e12-4e8f-8a55-03fa9d92f8c7)

The contents of each file before fixing the bug

content of MyArryaListPublicTester.java (no changes made to this for fixing error):

```
/**
     * Aims to test the rotate method when 
     * input index is in the range [0, length - 1]
     */
    @Test
    public void testRotateFullList() {
        listWithInt.rotate(0);
        System.out.println(listWithInt);
        for (Object x: listWithInt.values){
                System.out.println(x);
        }
        assertArrayEquals("check data", new Integer[]{1, 2, 3}, listWithInt.values);
        assertEquals("size should not get incremented", 3, listWithInt.length);

        System.out.println(listWithInt);
        for (Object x: listWithInt.values){
                System.out.println(x);
        }
        listWithInt.rotate(1);
        System.out.println(listWithInt);
        for (Object x: listWithInt.values){
                System.out.println(x);
        }
        assertArrayEquals("check data", new Integer[]{2, 3, 1}, listWithInt.values);
        assertEquals("size should not get incremented", 3, listWithInt.length);

        listWithInt.rotate(2);
        System.out.println(listWithInt);
        for (Object x: listWithInt.values){
                System.out.println(x);
        }
        assertArrayEquals("check data", new Integer[]{1, 2, 3}, listWithInt.values);
        assertEquals("size should not get incremented", 3, listWithInt.length);
    }

    /**
     * Aims to test the rotate method when 
     * input index is in the range [0, length - 1]
     */
    @Test
    public void testRotatePartialNullList() {
        Integer[] arrPartialNull = new Integer[]{null, 1, 2, null, null, 3, null, null};
        MyArrayList<Integer> listPartialNull = new MyArrayList<>(arrPartialNull);
        listPartialNull.length = 6;

        listPartialNull.rotate(1);
        assertArrayEquals("check data", new Integer[]{1, 2, null, null, 3, null, null, null}, listPartialNull.values);
        assertEquals("size should not get incremented", 6, listPartialNull.length);

        listPartialNull.rotate(3);
        assertArrayEquals("check data", new Integer[]{null, 3, null, 1, 2, null, null, null}, listPartialNull.values);
        assertEquals("size should not get incremented", 6, listPartialNull.length);

        listPartialNull.rotate(5);
        assertArrayEquals("check data", new Integer[]{null, null, 3, null, 1, 2, null, null}, listPartialNull.values);
        assertEquals("size should not get incremented", 6, listPartialNull.length);
```


