# Lab Report 5 by Sophia Yermolenko

---
### [A link to my group's markdown-parse repository](https://github.com/httrieu/markdown-parser)

## [FIRST TEST](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/22.md)

### **1. How our group found the test with different results:**

To find this test our group used vimdiff on the results of both the given implementation from the repository and our own implmementation. This was achieved by manually scrolling until we found the differences.

### **2. Describe which implementation is correct, or neither if both give the wrong output:**

Both implementations are incorrect. This is demonstrated by the screenshots below. 
This is shown on line 269 in my group's implementation and line 270 for the implementation from the repository. 

The correct output should look like this: `[ti\*tle]` since the format in markdown is the following: `[foo](/bar\* "ti\*tle")`. 

![image](lb5.jpg)

### **3. For the implementation that's not correct (or choose one if both are incorrect), describe the bug (the problem in the code) in about 2-3 sentences. You don't have to provide a fix, but you should be specific about what is wrong with the program, and show the code that should be fixed (Provide a screenshot of code and highlight where the change needs to be made).**

The screenshot of the code is provided at the bottom of this question. The issue with this code is that does not account for backslashes, and because of this, the entire line `[foo](/bar\* "ti\*tle")` gets ignored completely. When the parser does not find the next link, it returns an empty arraylist as seen by the outputs in the earlier screenshots. However, there was a link that should have been found by the parser and added to the arraylist.

![image](lb51.jpg)

---

## [SECOND TEST](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md)

### **1. How our group found the test with different results:**

This test is also included in the above screenshot. To find this test our group used vimdiff on the results of both the given implementation from the repository and our own implmementation. This was achieved by manually scrolling until we found the differences.
 
### **2. Describe which implementation is correct, or neither if both give the wrong output:**

Both implementations are incorrect again. My group's code unfortunately went into an infinite loop. This caused the parser to skip over the file without reading the contents. 
The implementation from the repository gave a link as the output, but the contents were incorrect. 
The incorrect output was: `[url]`
The correct output should look like this: `[title (with parens)]`

### **3. For the implementation that's not correct (or choose one if both are incorrect), describe the bug (the problem in the code) in about 2-3 sentences. You don't have to provide a fix, but you should be specific about what is wrong with the program, and show the code that should be fixed (Provide a screenshot of code and highlight where the change needs to be made).**

The original Markdown file contains the following code:
```
[Foo*bar\]]:my_(url) 'title (with parens)'

[Foo*bar\]]
```

As seen in the screenshot below, our group's parser only looks at the first closed parenthesis. This means that it might not know that the link is actually located in the following closed parenthesis, not necessarily after the first closed ones.

![image](lab52.jpg)

---
Thank you for reading!
