## CSE 15L Lab 4

# Step 4

**Logging into ieng6 account:**


<img width="445" alt="ieng6_log in" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/bfe09e5e-3c9b-4ad9-a62b-b3b8bdee44be">

Keys pressed: pressed `<enter>`, then typed out `ssh knalabotu@ieng6.ucsd.edu`, pressed `<enter>` and put in my password and then pressed `<enter>`

# Step 5

**Git Cloning:**

<img width="475" alt="git_clone" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/9c5b1b84-9d85-4573-9ae5-faebcacb3f0d">

Keys pressed: used `<enter>`and typed `git clone git@github.com:keerthinalabotu/cse15l-lab-reports.git` which was the ssh link for cloning. Pressed `<enter> again and it cloned. 

# Step 6

**Running tests, failing**

<img width="483" alt="errors_test sh" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/637e3381-e426-420d-aced-32a898bb70ea">

Keys pressed: Used `<enter>` to get to the next command, and then typed `cd lab7` to get into the `lab7` directory. Pressed `<enter>` to get to the next command and typed `bash test.sh` to run the tests and `<enter>`. Recieved the output shown in the screenshot above.  

# Step 7

**Editing code to make sure it works now**

<img width="518" alt="vim_edit" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/79bf4347-6ff5-42a8-8537-7562304968eb">

Keys pressed: In order to be able to edit the code and see what test was failing I first used `<enter>` to get to the next line and put in the command `ls` to see what differetn files were available. Pressed `<enter>` again and used `vim ListExamples.java` and `<enter>` to get the ability to edit the `ListExamples.java` file. Pressed `<up> <up> <up> <up> <up> <up>` `<l> <l> <l> <l> <l> <l> <l> <l> <l> <l> <l>` and then pressed `<i>` to insert and `2`. Then `<l>` and on top of the `1` I pressed `x` to delete it. Used `:wq` and `<enter>` to save and exit. 

# Step 8

**Run the tests to show that they work**

<img width="317" alt="bash_test" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/4b29a7b8-1775-4d6b-8c9f-18696de47058">

Keys pressed: Pressed `<enter>` again and put in the command `bash test.sh` and `<enter>` to run the tests (note: I could have also presesed `<up> <up> <up> <up>`. The tests passed (as shown in the screenshot).

# Step 9

**Commit changes through using `git add`, `git push`, and `git commit -m`**

<img width="466" alt="Screenshot 2024-02-27 085126" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/49c97082-eabc-4cf3-93f9-7fe1ce9268a6">

Keys pressed: Pressed `<enter>` and ran `git add`, `<enter>` to add all the changes. Then type `git commit -m 'fixed the issue'` and `<enter>` to commit the changes. Type `git push` and `<enter>`.

Function of these commands: 
- `git add` - this command queues in the changes that are to be made by the commit.
- `git commit -m ""` - this command commits the changes that were added into the local repository.
- `git push` - pushes local repository changes to a remote repository.

