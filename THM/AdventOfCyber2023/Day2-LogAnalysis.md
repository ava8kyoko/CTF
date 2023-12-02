# O Data, All Ye Faithful (Log Analysis)

## Learning Objectives

- In today’s task, you will:
- Get an introduction to what data science involves and how it can be applied in Cybersecurity
- Get a gentle (We promise) introduction to Python
- Get to work with some popular Python libraries such as Pandas and Matplotlib to crunch data
- Help McHoneyBell establish an understanding of AntarctiCrafts’ network


### Jupiter

<p>
Jupyter Notebooks are open-source documents containing code, text, and terminal functionality. They are popular in the data science and education communities because they can be easily shared and executed across systems. Additionally, Jupyter Notebooks are a great way to demonstrate and explain proof of concepts in Cybersecurity.

Jupyter Notebooks could be considered as instruction manuals. As you will come to discover, a Notebook consists of “cells” that can be executed one at a time, step by step. You’ll see an example of a Jupyter Notebook in the screenshot below. Note how there are both formatted text and Python code being processed:
</p>
<img width="967" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/be597e4c-ca43-414e-9283-a4ee22b59fe3">
<p>
Before we begin working with Jupyter Notebooks for today’s practicals, we must become familiar with the interface. Let’s return to the machine we deployed at the start of the task (pane on the right of the screen).
<img width="1099" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/1cdb76b8-458c-45f8-b632-e1a38c7f1f74">
You will be presented with two main panes. On the left is the “File Explorer”, and on the right is your “workspace”. This pane is where the Notebooks will open. Initially, we are presented with a “Launcher” screen. You can see the types of Notebooks that the machine supports. For now, let’s left-click on the “Python 3 (ipykernel)” icon under the “Notebook” heading to create our first Notebook.
</p>
<img width="1031" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/8a388a42-86c9-43f9-8283-6783ab63ca1c">
<p>
You can double-click the "Folder" icon in the file explorer to open and close the file explorer. This may be helpful on smaller resolutions. The Notebook’s interface is illustrated below:
</p>
<img width="1035" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/a8a8055c-84f8-44f1-9a83-ff9ae81e9bc8">
<p>
The notable buttons for today’s task include: 
</p>
<img width="1035" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/e8a81835-e6a8-4056-9135-63975d8c40f5">
<p>
For now, don’t worry about the toolbar at the very top of the screen. For brevity, everything has already been configured for you. Finally, note that you can move cells by clicking and dragging the area to their left:
</p>
<img width="919" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/c7b6e88e-d0c3-446a-a9ab-65f2096c5da1">

<img width="919" alt="image" src="https://github.com/ava8kyoko/CTF/assets/80278345/26c27262-e7e6-4618-be35-7f3f8c5a4162">

## Practical

### Python3 Crash Course

Remember to press the “Run Cell” button (Shift + Enter) as you progress through the Notebook.

#### Print
One of the first things you learn when learning a programming language is how to print text. Python makes this extremely simple by using `print(“your text here”)`.

```
C:\Users\CMNatic>python
Python 3.10.10 (tags/v3.10.10:aad5f6a, Feb  7 2023, 17:20:36) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello World")
Hello World
```

#### Variable

The structure of a variable looks like this: `label = data`.

```
# age is our label (variable name).
# 23 is our data. In this case, the data type is an integer.
age = 23

# We will now create another variable named "name" and store the string data type.
name = "Ben" # note how this data type requires double quotations.
```

```
C:\Users\CMNatic>python
Python 3.10.10 (tags/v3.10.10:aad5f6a, Feb  7 2023, 17:20:36) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> name = "Ben"
>>> print(name)
Ben
```

#### Lists

Lists are an example of a data structure in Python. Lists are used to store a collection of values as a variable. For example: transport = ["Car", "Plane", "Train"] age = ["22", "19", "35"]

Note the terminal snippet below is for demonstration only.

```
Creating and printing a list in Python
C:\Users\CMNatic>python
Python 3.10.10 (tags/v3.10.10:aad5f6a, Feb  7 2023, 17:20:36) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> transport = ["Car", "Plane", "Train"]
>>> print(transport)
['Car', 'Plane', 'Train']
 ```

#### Python: Pandas

Pandas is a Python library that allows us to manipulate, process, and structure data. It can be imported using import pandas. In today’s task, we are going to `import Pandas` as the alias "pd" to make it easier to refer to within our program. This can be done via  `import as pd`.

There are a few fundamental data structures that we first need to understand.

## Series

<p>
In pandas, a series is similar to a singular column in a table. It uses a key-value pair. The key is the index number, and the value is the data we wish to store. To create a series, we can use Panda's Series function. First, let's:

Create a list: `transportation = ['Train', 'Plane', 'Car']`
<br>
Create a new variable to store the series by providing the list from above: `transportation_series = pd.Series(transportation)`
<br>
Now, let's print the series: `print(transportation_series)`
</p>

| Key (Index) |	Value |
| --- | --- |
0 |	Train
1	| Plane
2	| Car








