# Week 8 Lab Report

[MarkdownParse Repository](https://github.com/akluu/markdown-parser)

[Reviewed Repository](https://github.com/philliptwu/markdown-parser)

## Snippet 1:
___

### **Code:**

```md
[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

### **VScode Preview:**

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%205.01.57%20PM.png)

<table>
  <thead>
    <tr>
      <th>Expected Output</th>
      <th>Personal Output(Failed)</th>
      <th>Reviewed Output(Failed)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>[‘google.com, google.com, ucsd.edu]</td>
      <td>[url.com, `google.com, google.com]</td>
      <td> [url.com, `google.com, google.com]</td>
    </tr>
  </tbody>
</table>

#### **Test Code:**
```java
 @Test
    public void snippet1Test() throws IOException{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet1.md"); 
        String content = Files.readString(fileName);
        String[] split = content.split("\n");
        ArrayList<String> links = new ArrayList<String>();
        for(String s: split){
            String link = MarkdownParse.getLinks(s);
            if(link != null && MarkdownParse.isValidLink(link)){
                links.add(MarkdownParse.getLinks(s));
            }
        }

        ArrayList<String> res = new ArrayList<String>();
        res.add("'google.com");
        res.add("google.com");
        res.add("ucsd.edu");
        assertEquals(res, links);
    }

    @Test
    public void snippet1ReviewTest() throws IOException{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet1.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParseReview.getLinks(content);

        ArrayList<String> res = new ArrayList<String>();
        res.add("'google.com");
        res.add("google.com");
        res.add("ucsd.edu");
        assertEquals(res, links);
    }
```
#### **JUnit Output:**
![image](report4screenshots/Screen%20Shot%202022-05-22%20at%205.35.26%20PM.png)

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%205.35.52%20PM.png)

> I think only a small change to the code will be necessary to fix the backtick cases. I would only need to look for backticks between openParen and closedParen.


## Snippet 2:
___
### **Code:**

```md
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

### **VScode Preview:**

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%205.18.33%20PM.png)

| Expected Output | Personal Output(Failed) | Reviewed Output(Failed) |
| :---: | :---: | :----:|
|[a.com, a.com((, example.com]| [a.com, a.com((]  | [a.com, a.com((] |

#### **Test Code:**
```java
  @Test
    public void snippet2Test() throws IOException{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet2.md"); 
        String content = Files.readString(fileName);
        String[] split = content.split("\n");
        ArrayList<String> links = new ArrayList<String>();
        for(String s: split){
            String link = MarkdownParse.getLinks(s);
            if(link != null && MarkdownParse.isValidLink(link)){
                links.add(MarkdownParse.getLinks(s));
            }
        }

        ArrayList<String> res = new ArrayList<String>();
        res.add("a.com");
        res.add("a.com((");
        res.add("example.com");
        assertEquals(res, links);
    }

    @Test
    public void snippet2ReviewTest() throws IOException{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet2.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParseReview.getLinks(content);

        ArrayList<String> res = new ArrayList<String>();
        res.add("a.com");
        res.add("a.com((");
        res.add("example.com");
        assertEquals(res, links);
    }
```
#### **JUnit Output:**
![image](report4screenshots/Screen%20Shot%202022-05-22%20at%206.02.41%20PM.png)

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%206.06.58%20PM.png)

> I think only a small change to the code will be necessary to fix the backslash cases. I would only need to look for backslashes between openParen and closedParen.



## Snippet 3:
___
### **Code:**

```md
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text

```

### **VScode Preview:**

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%205.18.45%20PM.png)

| Expected Output | Personal Output(Failed) | Reviewed Output(Failed) |
| :---: | :---: | :----:|
|[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]| []  | ![image](report4screenshots/Screen%20Shot%202022-05-22%20at%206.14.51%20PM.png)|

#### **Test Code:**
```java
 @Test
    public void snippet3Test() throws Exception{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet3.md"); 
        String content = Files.readString(fileName);
        String[] split = content.split("\n");
        ArrayList<String> links = new ArrayList<String>();
        for(String s: split){
            String link = MarkdownParse.getLinks(s);
            if(link != null && MarkdownParse.isValidLink(link)){
                links.add(MarkdownParse.getLinks(s));
            }
        }

        ArrayList<String> res = new ArrayList<String>();
        res.add("https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule");
        assertEquals(res, links);

    }

    @Test
    public void snippet3ReviewTest()throws Exception{
        Path fileName = Path.of("/Users/andy/Desktop/cse15l/markdown-parser/Lab4MarkdownSnippets/snippet3.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParseReview.getLinks(content);

        ArrayList<String> res = new ArrayList<String>();
        res.add("https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule");
        assertEquals(res, links);
    }
```
#### **JUnit Output:**
![image](report4screenshots/Screen%20Shot%202022-05-22%20at%206.16.01%20PM.png)

![image](report4screenshots/Screen%20Shot%202022-05-22%20at%206.16.14%20PM.png)

> I think a more involved change would be required to fix this issue. My code reads each line instead of the entire text so multi-line links would not be a simple issue to resolve.


