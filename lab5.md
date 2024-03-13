## CSE 15L Lab 4

**Student Question:**

Hello,

My implementation for Rotating an array list is not working when I run my bash grade.sh. I believe it might have something to do with how I'm accessing values within the copy array and assign them to the values array. 

The errors I received when running the `bash grade.sh` was this: 
![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/4ae615d0-2eb0-4f8a-b3d5-55584b596f86)

This might be since I pass in the value `i` within this code for `copy[i]` but it might be counterintiuitive since the whole point is to update the value of index added in which I had forgotten to do, so I might need to add the index there as well. 

The test cases that caused the errors were the following: 

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/d1cb69a4-1e8a-488f-9e96-b0fcc6960027)

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e3f5d880-0f12-43c5-bc2d-6beb1c6b32e4)

I'm not too sure what is causing my error or if I have the correct assumption of what my error is. 

For reference, this is my code for my `rotate` method: 

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/76dcf30f-35a6-4a85-a7f3-89544739c7bf)

Thank you for your time!

_____________________________________________________________________________________

**TA response:**

Hi!

Your code looks really good so far! Something you might want to keep in mind is that for your second if loop you're not necessarily changing anything since you are passing in `i` for the index of copy that you are putting into values. But, notice that in your previous if loop you had just copied that over to your `copy` array. 

After you fix that index with what you really want to update values with, something else to keep in mind is that you might get an `index out of bounds` error so you may have to figure out a way to solve that (hint: you can use `mod` to try and solve the index out of bounds).

Hopefully this helps a bit!

-TA
__________________________________________________________________________________________

**Information that student got from trying this:**

The student probably understood from this that the value that they pass into the copy[] for the second if loop is never updated with the "index" that they are supposed to add. They also don't take into account the index out of bounds which they will eventually see as a problem when they see their terminal output.

After making a change to their code:

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/b4f5f2bf-0ba6-4d5b-812e-005db231d212)

Terminal output:

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e56ec222-d56c-4f25-ba5d-2f18a332a04c)

________________________________________________________________________

# Information needed about setup:

**The file & directory structure needed**

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

Content of MyList.java (not necessary for this bug/no changes made to this):

```
/**
 * This file contains all of the methods for the MyList interface. All classes
 * implementing this interface should also implement the methods listed here.
 */

/**
 * An interface that specifies the functionality of an ArrayList ADT
 */
public interface MyList<E> {
    /**
     * Increase the capacity of underlying array if needed
     *
     * @param requiredCapacity minimum capacity after expanding
     */
    void expandCapacity(int requiredCapacity);

    /**
     * Get the amount of elements array can hold
     *
     * @return number of elements that can be held
     */
    int getCapacity();

    /**
     * Add an element at the specified index
     *
     * @param index   position to insert the element
     * @param element the element to insert
     */
    void insert(int index, E element);

    /**
     * Add an element to the end of the list
     *
     * @param element the element to append
     */
    void append(E element);

    /**
     * Add an element to the beginning of the list 
     *
     * @param element the element to prepend
     */
    void prepend(E element);

    /**
     * Get the element at the given index
     *
     * @param index the index at which to return the element
     * @return the element at the index
     */
    E get(int index);

    /**
     * Replaces an element at the specified index with a new element and return
     * the original element
     *
     * @param index   the index at which to replace
     * @param element the element with which to replace
     * @return the original element
     */
    E set(int index, E element);

    /**
     * Remove the element at the specified index and return the removed element
     *
     * @param index the index at which to remove the element
     * @return the removed element
     */
    E remove(int index);

    /**
     * Get the number of elements in the list
     *
     * @return number of elements in the list
     */
    int size();

    /**
     * Rotate the list by index number of positions to the left
     * 
     * @param index the number of positions to rotate by
     */
    void rotate(int index);

    /**
     * Find the element in the list and return its index
     * 
     * @param element the element to find
     * @return the index of the first occurrence of element (-1 if not found)
     */
    int find(E element);
```
Content of MyArrayList.java before fixing the bug:

```
/*
   Name: Keerthi Nalabotu
   Email: knalabotu@ucsd.edu
   PID: A17798652
   Sources used: Tutors

   This file is used to create a MyArrayList class to implement what a java
   ArrayList class would be like. The class contains methods for ArrayList 
   such as get, set, and other basic functiosn that an Array List should have.
 */

/**
 * This class stores an array of Objects as well as an int of length. The class
 * is able to perform actions on the values array as if it was an Array List. 
 * 
 * Instance Variables:
 * values - An array that will store Objects put into it.
 * length - The value for the valid arguments in the values array.
 */

public class MyArrayList<E> implements MyList<E>{

    /** Constants (Magic Numbers): 5 */
    // Default capacity
    private static final Integer DEFAULT_CAPACITY = 5;
    private static final Integer EXPAND_CAPACITY = 2;

    //Instance Variables
    Object[] values; //this is the first instance variable
    int length; //length of values?
    


    /**
     * The first version of the constructor initializes the values array to
     * a default length of 5 Objects if nothing is passed into the constructor.
     */
    public MyArrayList(){
        this.values = new Object[DEFAULT_CAPACITY];
        //this.length = 5;
    }

    /**
     * The second version of the constructor initializes the values array to
     * a default length of initial Capacity and also checks 
     * if the intialCapacity is valid.
     * 
     * @param initialCapacity  Value to set the Capacity of the values array
     */
    public MyArrayList(int initialCapacity){
        if (initialCapacity<0){
            throw new IllegalArgumentException();
        }
        this.values = new Object[initialCapacity];
    }

    /**
     * The third version of the constructor initializes the values array to
     * an array and creates a shallow copy of the array passed in for 
     * values. It also does a null check and sets it to a default 
     * length of 5 if null is passed in.
     * 
     * @param arr  Value to set values equal to (by using a shallow copy)
     */
    public MyArrayList( E[] arr){
        if (arr == null){
            this.values = new Object[DEFAULT_CAPACITY];
        }
        else{
            this.values = arr;
            length= arr.length;
        }
        
    }

    /**
     * This method expands the capacity of the values array based on 
     * what is passed in as an argument.
     * 
     * @param requiredCapacity This is number that is required for the capacity.
     */

    public void expandCapacity(int requiredCapacity){ 

        if (requiredCapacity<this.values.length){
            throw new IllegalArgumentException();
        }

        if (this.values.length !=0){
            Object [] newValues = new Object[values.length*EXPAND_CAPACITY]; 
            for (int i = 0; i<this.values.length; i++){
                newValues[i]=values[i];
            }
            values = newValues;
            
        }
        if (this.values.length ==0){ 
            Object[] newValues = new Object[DEFAULT_CAPACITY];
            values =newValues;
        }
        if (this.values.length<requiredCapacity){
            Object [] newValues = new Object[requiredCapacity];
            for (int i = 0; i<this.values.length; i++){
                newValues[i]=values[i];
            }
            values = newValues;
        }
        
    }

    /**
     * This method returns the capacity of the values array.
     *
     * @return capacity of values
     */
    
    public int getCapacity(){
        return this.values.length;
    }


    /**
     * This method inserts an element in the index that is required
     * in the values array.
     * 
     * @param index This is the location that element should be inserted
     * @param element This is the element we want to insert into the array.
     */
    public void insert(int index, E element){
        if (index<0 || index>this.values.length 
            || index>this.length){
            throw new IndexOutOfBoundsException();
        }


        if (this.length == this.values.length){
            this.expandCapacity(this.values.length+1); 
        }

        
        for (int i =this.length; i>index; i--){
            values[i]=values[i-1];
            
        }
        values[index]=element;

        this.length+=1;
    }


    /**
     * This method adds an element at the end of the values array.
     * 
     * @param element This is the element that we want to add at 
     * the end of values.
     */
    public void append(E element){
        if (this.length == this.values.length){
            this.expandCapacity(this.values.length+1); 
        }

        values[this.length]=element;
        this.length+=1;

    }

    /**
     * This method adds an element at the beginning of the array.
     * 
     * @param element This is the element that we want to add at the beginning.
     */
    public void prepend(E element){

        if (this.length == this.values.length){
            this.expandCapacity(this.values.length+1); 
        }

        //we just implement the insert method since prepending is
        //basically the same thing as inserting at index 0.
        this.insert(0, element); 
        
    }

    /**
     * This method gets the element at the index passed into the array.
     * 
     * @param index This is the index of the element we want to get.
     * @return The value in the index we desire.
     */
    public E get(int index){

        return (E) this.values[index];

    }

    /**
     * This method sets the element passed in to the index passed in.
     * 
     * @param index This is the index we want to set element to.
     * @param element This is the element we want to pass in.
     * @return returns the overwitten element
     */
    public E set(int index, E element){
        
        Object overwritten = values[index];
        values[index]= element;
        return (E) overwritten;

    }

    /**
     * This method removes the element at the given index.
     * 
     * @param index This is the index of the value that needs to be removed.
     * @return returns the value that we're removing
     */
    public E remove(int index){
        if (index<0 || index>this.values.length 
            || index>this.length){
            throw new IndexOutOfBoundsException();
        }
        
        values[index]= null;

        //this code basically sets every current place 
        //to the next one (you set the curent index to null so its removed).
        for (int i =index; i<this.length-1; i++){
            values[i]=values[i+1];
        }
        values[this.length-1]=null;

        this.length-=1;
        return (E) values;
    }

    /**
     * This returns the size of values which is all the valid items 
     * represented by length.
     * 
     * @return this returns the size 
     * 
     */
    public int size(){
        return this.length; // since its asking to return 
        //the valid elements you would return the length not this.values.length
    }

    /**
     * This method rotates the array by the index passed in.
     * 
     * @param index This is the index representing how much we need to move
     * the array to the left.
     */
    public void rotate(int index){
        if (index<0 || index>this.values.length || 
            index>this.length ||this.length ==0){
            throw new IndexOutOfBoundsException();
        }

        Object [] copy = new Object[values.length];
        
        for (int i=0; i<this.length; i++){
            copy[i]=values[i];
        }

        for (int i =0; i<this.length; i++){
            values[i]=copy[i+index];
        }
    }

    /**
     * This method find the index of the element passed in
     * 
     * @param element This is the element that we want to find within values.
     * @return returns -1 if the value is not in the array.
     */
    public int find (E element){
        for (int i=0; i<this.values.length; i++){
            if (values[i]==element){
                return i;
            }
        }
        return -1;
    }
}
```

**The full command line (or lines) you ran to trigger the bug**
- bash test.sh

- ![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/369854b2-b2b7-479e-a545-f17581f9fe78)


**A description of what to edit to fix the bug**

- To fix the error we change the value we use to access a value within the copy array. Originally we had copy[i] in the second if loop. We change that to copy[(i+index)%this.length].

  
- ![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/9eaa525f-fa11-4502-97a6-d878bd955aa4)

**When we run the tests again we pass all of them:**

![image](https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/5a0325e4-cb1d-45b7-99c8-f3aa1137b189)

________________________________________________________________________________________

# Reflection:

Something cool that I learned this quarter was using vim. I had no idea that we could edit code directly in the terminal and I thought that was really cool (even though editing the code is a bit hard using the "i" and "x"). It was interesting that it's accessible through a local editor like vscode or wherever you want to edit it.

In addition, I also never really knew how to use git commands so I found it to be cool how I could save the edits that I made directly from my local machine to the github, making it accessible to people using the github repo. 











