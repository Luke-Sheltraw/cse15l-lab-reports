# Lab Report 2 - _Week 4_
## Debugging

***

### **Code Change 1**

**Accounting for non-link text at the end of input file.**

*Change to file on [GitHub](https://github.com/Luke-Sheltraw/markdown-parser/commit/113da7e36253465dcd9df5ce7825d539a508e8b1)*:
[![screenshot of difference](images/codediff1.png)](https://github.com/Luke-Sheltraw/markdown-parser/commit/113da7e36253465dcd9df5ce7825d539a508e8b1)

*Failure-inducing input on [GitHub](https://github.com/Luke-Sheltraw/markdown-parser/commit/c0ec2021c551959d066001ce0e3a9c412b2c6604)*:
[![screenshot of failure-inducing file](images/failurefile1.png)](https://github.com/Luke-Sheltraw/markdown-parser/commit/c0ec2021c551959d066001ce0e3a9c412b2c6604)

*Symptom*:
```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:19)
        at MarkdownParse.main(MarkdownParse.java:30)
```
*Expected output*:
```
[https://something.com, some-thing.html]
```

*Description*:

The bug here is that the code assumed that the final text in the file would be a link. Thus, when such was not the case in our failure-inducing input file (i.e. the single closing bracket at the very end of the file), the code showed the symptom of an OutOfMemoryError, or an infinite loop. This makes sense, as .indexOf() returns -1 for a String that is not found, and the loop sets the currentIndex to be 1 greater than the index of the most recent closing parenthesis—resulting in a currentIndex of 0 whenever it can't find a closing parenthesis. The while-loop runs until currentIndex if equal to or greater than the length of the text, meaning it runs forever if there is text that isn't a link at the end of the file. We fixed this by breaking the while-loop if it can't find all the components necessary for a link in the correct order.  

***

### **Code Change 2**

***

### **Code Change 3**
