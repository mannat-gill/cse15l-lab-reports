# **Welcome to my Lab Report 2 Page !**

# Lab 2 : Servers and Bugs 

## Part 1: Servers
## Part 2: Bugs 

>## 1. 
```
Linked List: Append Method
__________________________

FAILURE INDUCING INPUT : A linked list with elements {2, 3, 4}

![Image](LL_Append_FII.png)

SYMPTOM : A infinite while loop ran, because n.next was being set to a new Node instead rather than outside the loop. --> Resulted in an error of "Java heap space"

![Image](LL_Append_Symptom.png)

BUG : move  "n.next = new Node(value, null);" from in the while loop to outside the while loop 

![Image](LL_Append_Bugs.png)

CHANGED : method after making change

![Image](LL_Append_Changed.png)

```
>## 2. 
```
Files: GetFiles Method
__________________________

FAILURE INDUCING INPUT : A list of files paths 

![Image](Files_GetFiles_FII.png)
![Image](Files_GetFiles_FII2.png)


SYMPTOM :

![Image](Files_GetFiles_Symptoms.png)

BUG :

![Image](Files_GetFiles_Bugs.png)

CHANGED : 

![Image](Files_GetFiles_Changed.png)

```