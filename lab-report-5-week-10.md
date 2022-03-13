> # **Differences:**
![](diff.png)
The results of testing the test files were saved to text files, where `diff` was run on them.

---
> # **Line 212 (test-files/194.md):**
### **Difference:**
![](194.png)
### **Professor's:**
![](194p.png)
### **Group's:**
![](194m.png)

I would say that the professor's implementation is correct as despite there being a gap between the `]` and the `(`, markdown still seems to accept this as a valid input.

As a result, we should remove the check found in the `if` statement here:
![](194e.png) 

---
> # **Line 878 (test-files/494.md):**
### **Difference:**
![](494.png)
### **Professor's:**
![](494p.png)
### **Group's:**
![](494m.png)
### **Correct:**
![](494r.png)

Although both seem to be wrong, I would say that the professor's implementation is slightly more accurate with his inclusion of: 

![](494a.png)

which allows for parentheses to found in the link. To help fix this, we should include code similiar to our groups's which checks for `\` right before `]`:

![](494b.png)

The similar code should check for `\` before `(` and `)` and should accordingly not included (or include) itself.
