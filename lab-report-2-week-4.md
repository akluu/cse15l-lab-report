# Week 4 Lab Report

## Original MarkdownParse.java Code
```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.ArrayList;

public class MarkdownParse {

    public static ArrayList<String> getLinks(String markdown) {
        ArrayList<String> toReturn = new ArrayList<>();
        // find the next [, then find the ], then find the (, then read link upto next )
        int currentIndex = 0;
        while(currentIndex < markdown.length()) {
            int openBracket = markdown.indexOf("[", currentIndex);
            int closeBracket = markdown.indexOf("]", openBracket);
            int openParen = markdown.indexOf("(", closeBracket);
            int closeParen = markdown.indexOf(")", openParen);
            toReturn.add(markdown.substring(openParen + 1, closeParen));
            currentIndex = closeParen + 1;
        }

        return toReturn;
    }


    public static void main(String[] args) throws IOException {
        Path fileName = Path.of(args[0]);
        String content = Files.readString(fileName);
        ArrayList<String> links = getLinks(content);
	    System.out.println(links);
    }
}
```

## First Change
---
![Image](screenshots/Screen%20Shot%202022-04-24%20at%203.56.46%20PM.png)

**These changes resolved the failure-inducing inputs in [this](https://github.com/akluu/markdown-parser/blob/main/newTest.md) test file.**

| Output Before| Output After |
|:---:|:---:|
| `[https://test.com, www.fakelink.com, www.facebook.com]` | `[https://test.com, www.facebook.com]` |

> These changes made the program read individual lines in the md file. This helped resolve some of the initial bugs from reading the entire as a string. As we can see from the outputs, the program no longer falls for the trap fake links in the test file and only collects valid links.

## Second Change
---
![Image](screenshots/Screen%20Shot%202022-04-24%20at%204.19.57%20PM.png)

**These changes resolved the failure-inducing inputs in [this](https://github.com/akluu/markdown-parser/blob/main/newTest2.md) test file.**

| Output Before| Output After |
|:---:|:---:|
| `[https://test.com, www.fakelink.com, www.facebook.com]` | `[https://test.com, www.facebook.com]` |

> The previous changes did not resolve a bug that read fake links when the links were within the same line. So, this change to the code resolved the symptom described.

## Third Change
---
![Image](screenshots/Screen%20Shot%202022-04-24%20at%204.20.32%20PM.png)

**These changes resolved the failure-inducing inputs in [this](https://github.com/akluu/markdown-parser/blob/main/newTest3.md) test file.**

| Output Before| Output After |
|:---:|:---:|
| `[https://test.com, www.facebook.com, fakeImage.png]` | `[https://test.com, www.facebook.com]` |

> The program still included a bug where the program would collect links to images. The change above resolved this issue and only collected website links when image links are present in the test file.
