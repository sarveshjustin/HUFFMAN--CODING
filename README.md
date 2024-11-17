# EXP 11 Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Initialize the string.


### Step2:
Create the tree nodes.

### Step3:
Implement the Huffman Code.

### Step4:
Calculate the Frequency.

### Step5:
Print the Huffman code for the string.

 
## Program:
```
Name:sarvesh s
Reg No:212222230135
```
#### Get the input String
``` py
string = 'sarvesh'
```
#### Create tree nodes
``` Python
class NodeTree(object):
    
    def __init__(self, left=None, right=None):
        self.left = left 
        self.right  = right

    def children(self):
        return (self.left,self.right)
```
#### Main function to implement huffman coding
``` Python
def huffman_code_tree(node, left=True, binString=''): 
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    D= dict()
    D.update(huffman_code_tree(l, True, binString + '0'))
    D.update(huffman_code_tree(r, False, binString + '1'))
    return D
```
#### Calculate frequency of occurrence
``` Python
freq = {}

for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1

freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes = freq

while len(nodes) > 1:
    (key1, c1) = nodes[-1]
    (key2, c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1, key2)
    nodes.append((node, c1 + c2))
    
    nodes = sorted(nodes, key=lambda x: x[1],reverse=True)

```
#### Print the characters and its huffmancode
``` Python
huffmanCode = huffman_code_tree (nodes[0][0])
print('Char | Huffman code ')
print('---------------------')

for (char, frequency) in freq:
    print('%-4r %12s' % (char, huffmanCode[char]))

```
## Output:

### Print the characters and its huffmancode
![image](https://github.com/user-attachments/assets/0f5e1869-235d-4bd5-a48d-bb0a4f192c83)


## Result
Thus the huffman coding was implemented to compress the data using python programming.
