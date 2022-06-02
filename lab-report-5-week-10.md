# Week 10 Lab Report

## **Finding Different Test Results**
1.  Using the bash script:
```shell
javac MarkdownParse.java
javac MarkdownParsePersonal.java
for file in test-files/*.md;
do
  echo $file >> results.txt
  echo $file >> personalResults.txt
  java MarkdownParse $file >> results.txt
  java MarkdownParsePersonal $file >> personalResults.txt
done
```
2. Then run `vimdiff results.txt personalResults.txt` to get:

![image](report5screenshots/Screen%20Shot%202022-06-01%20at%205.23.21%20PM.png)

>Here are the highlighted line show the differences between the two result files and we can find different tests.

## **First Test**

[Link to test file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/14.md)

### **Output:**

![image](report5screenshots/Screen%20Shot%202022-06-01%20at%205.52.55%20PM.png)

### **Preview:**

![image](report5screenshots/Screen%20Shot%202022-06-01%20at%205.55.55%20PM.png)

**Therefore, the expected output should be: []**

>The implementation that had a bug was the implemenatation given to us from the lab. In this implementation, getlinks does not account for backslahes, so it wrongly added a link to the output.

## **Second Test**

[Link to test file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/577.md)

### **Output:**

![image](report5screenshots/Screen%20Shot%202022-06-01%20at%206.06.29%20PM.png)

### **Preview:**

![image](report5screenshots/Screen%20Shot%202022-06-01%20at%206.08.45%20PM.png)

**Therefore, the expected output should be: []**

>The implementation that had a bug was the implemenatation given to us from the lab. In this implementation, getlinks does not account for images, so it wrongly added a link to the output.
