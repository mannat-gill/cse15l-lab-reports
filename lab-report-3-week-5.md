# **Welcome to my Lab Report 3 Page !**

# Week 5 Lab Report: The many fun ways to use 'find' 

## less -p[string] [file path]
-------------------------

This command highlights any occurence of the string you passed within the given file. It also directly goes to the first occurence of the string in the file. This is useful for when trying to find if a certain string exits in a file and where it is located, especially when trying to find its first occurence. 

### Example 1:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -psystem technical/911report/chapter-1.txt
```
Output

![Image](Lab_Report_3_Photos/less_-p_Ex_1.png)

In this case we see that we were searching for the substring "system". So it highlighted wherever it found "system" within the file. 

### Example 2:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -pPurification technical/plos/pmed.0020161.txt
```

Output

![Image](Lab_Report_3_Photos/less_-p_Ex_2.png)

In this example we were searching for "Purification" in this file. However it did not find any occurence of that string. In such cases we get the above output. Something to notice is that although "Purification" wasn't found, "purififcation" is in the file. This just shows that it is case-sensitive.

### Example 3:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -pthe technical/plos/pmed.0020161.txt
```

Output

![Image](Lab_Report_3_Photos/less_-p_Ex_3.png)

Over here something noticable is that it finds ALL occurences of the string we are searching for, since "the" is highlighted multiple times. 

## less -N [file path]
-------------------------

The purpose of this command is to display the line numbers along with the contents of the file. This is great for when you need to reference certain lines in the file, because it makes it easier to skim through without having to count each line manually. 


### Example 1:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -N technical/911report/chapter-1.txt   
```
Output

![Image](Lab_Report_3_Photos/less_-N_Ex_1.png)

The image above displays the use of -N in the file chapter-1.txt. Something to pay attention to is that lines with a bunch of characters will wrap over to the next line and maintain the line number. An example of this is line 6, it gets carried over twice. 

### Example 2:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -N technical/biomed/1468-6708-3-7.txt

```

Output

![Image](Lab_Report_3_Photos/less_-N_Ex_2.png)

Some files can be very long, such as in this case going up to line 317, which is why displaying line numbers can be helpful in certain situations. 


### Example 3:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -N technical/government/Alcohol_Problems/DraftRecom-PDF.txt
```

Output

![Image](Lab_Report_3_Photos/less_-N_Ex_3.png)


 Not only does displaying the line number help to traverse through the file easily, when you know what line you are searching for, but it is also helpful to get an idea of how big a file might be. 

## less -X [file path]
-------------------------

This command leaves the contents of the file in the terminal after exiting. You can also use the down arrow to control how much of the file you want to display after exiting. This is useful for when you need to reference back to something in the file when you are in the terminal. 


### Example 1:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -X technical/911report/chapter-2.txt  
```
Output

![Image](Lab_Report_3_Photos/less_-X_Ex_1.png)

Since -X allows you to decide how much of the file you want to display on the terminal, you have total control. With this you can adjust the length to your preference, which can be helpful in cases where you might want to just see a snippet of the file or even a large portion of it. 

### Example 2:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -X technical/government/Alcohol_Problems/DraftRecom-PDF.txt

```

Output

![Image](Lab_Report_3_Photos/less_-X_Ex_2.png)

With the contents being in the terminal, if you need to reference back you can just do that by scrolling. 

### Example 3:

Input:
```
mannat@MacBook-Pro-2 docsearch % less -X technical/government/Media/5_Legal_Groups.txt
```

Output

![Image](Lab_Report_3_Photos/less_-X_Ex_3.png)


 As you can see, at the bottom of each picture it shows "mannat@MacBook-Pro-2 docsearch %", which means I am back in the terminal and at the same time some portion of the file is still displayed directly above. 