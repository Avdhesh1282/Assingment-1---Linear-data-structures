# Assingment-1---Linear-data-structures



# Python3 implementation of simple method
# to find count of pairs with given sum.
#questions -1
 def getPairsCount(arr, n, sum):
 
    count = 0  # Initialize result
 
    # Consider all possible pairs
    # and check their sums
    for i in range(0, n):
        for j in range(i + 1, n):
            if arr[i] + arr[j] == sum:
                count += 1
 
    return count
    
    
  #questions 2     # Iterative python program to reverse an array
 
# Function to reverse A[] from start to end
def reverseList(A, start, end):
    while start < end:
        A[start], A[end] = A[end], A[start]
        start += 1
        end -= 1
 
# Driver function to test above function
A = [1, 2, 3, 4, 5, 6]
print(A)
reverseList(A, 0, 5)
print("Reversed list is")
print(A) 

# Python program to check if strings are rotations of
# each other or not
 
# Function checks if passed strings (str1 and str2)
# are rotations of each other
def areRotations(string1, string2):
    size1 = len(string1)
    size2 = len(string2)
    temp = ''
 
    # Check if sizes of two strings are same
    if size1 != size2:
        return 0
 
    # Create a temp string with value str1.str1
    temp = string1 + string1
 
    # Now check if str2 is a substring of temp
    # string.count returns the number of occurrences of
    # the second string in temp
    if (temp.count(string2)> 0):
        return 1
    else:
        return 0
#questions 3 
# Driver program to test the above function
string1 = "AACD"
string2 = "ACDA"
 
if areRotations(string1, string2):
    print ("Strings are rotations of each other")
else:
    print ("Strings are not rotations of each other")
#questions 4 
Python program to print the first non-repeating character
NO_OF_CHARS = 256
 
# Returns an array of size 256 containing count
# of characters in the passed char array
def getCharCountArray(string):
    count = [0] * NO_OF_CHARS
    for i in string:
        count[ord(i)]+= 1
    return count
 
# The function returns index of first non-repeating
# character in a string. If all characters are repeating
# then returns -1
def firstNonRepeating(string):
    count = getCharCountArray(string)
    index = -1
    k = 0
 
    for i in string:
        if count[ord(i)] == 1:
            index = k
            break
        k += 1
 
    return index
 
# Driver program to test above function
string = "geeksforgeeks"
index = firstNonRepeating(string)
if index == 1:
    print ("Either all characters are repeating or string is empty")
else:
    print ("First non-repeating character is" , string[index])
 
 #questions 5
  Recursive Python function to solve tower of hanoi
 
def TowerOfHanoi(n , from_rod, to_rod, aux_rod):
    if n == 0:
        return
    TowerOfHanoi(n-1, from_rod, aux_rod, to_rod)
    print("Move disk",n,"from rod",from_rod,"to rod",to_rod)
    TowerOfHanoi(n-1, aux_rod, to_rod, from_rod)
         
# Driver code
n = 4
TowerOfHanoi(n, 'A', 'C', 'B')
# A, C, B are the name of rods

#questions 6
# Write Python3 code here
# -*- coding: utf-8 -*-
 
# Example Input
s = "*-A/BC-/AKL"
 
# Stack for storing operands
stack = []
 
operators = set(['+', '-', '*', '/', '^'])
 
# Reversing the order
s = s[::-1]
 
# iterating through individual tokens
for i in s:
 
    # if token is operator
    if i in operators:
 
        # pop 2 elements from stack
        a = stack.pop()
        b = stack.pop()
 
        # concatenate them as operand1 +
        # operand2 + operator
        temp = a+b+i
        stack.append(temp)
 
    # else if operand
    else:
        stack.append(i)
 
# printing final output
print(*stack)

#questions 7
# Python Program to convert prefix to Infix
def prefixToInfix(prefix):
    stack = []
     
    # read prefix in reverse order
    i = len(prefix) - 1
    while i >= 0:
        if not isOperator(prefix[i]):
             
            # symbol is operand
            stack.append(prefix[i])
            i -= 1
        else:
           
            # symbol is operator
            str = "(" + stack.pop() + prefix[i] + stack.pop() + ")"
            stack.append(str)
            i -= 1
     
    return stack.pop()
 
def isOperator(c):
    if c == "*" or c == "+" or c == "-" or c == "/" or c == "^" or c == "(" or c == ")":
        return True
    else:
        return False
 
# Driver code
if __name__=="__main__":
    str = "*-A/BC-/AKL"
    print(prefixToInfix(str))
    
#questions 8
# Python3 program to check for
# balanced brackets.
 
# function to check if
# brackets are balanced
 
 
def areBracketsBalanced(expr):
    stack = []
 
    # Traversing the Expression
    for char in expr:
        if char in ["(", "{", "["]:
 
            # Push the element in the stack
            stack.append(char)
        else:
 
            # IF current character is not opening
            # bracket, then it must be closing.
            # So stack cannot be empty at this point.
            if not stack:
                return False
            current_char = stack.pop()
            if current_char == '(':
                if char != ")":
                    return False
            if current_char == '{':
                if char != "}":
                    return False
            if current_char == '[':
                if char != "]":
                    return False
 
    # Check Empty Stack
    if stack:
        return False
    return True
 
 
# Driver Code
if __name__ == "__main__":
    expr = "{()}[]"
 
    # Function call
    if areBracketsBalanced(expr):
        print("Balanced")
    else:
        print("Not Balanced")
 
 
 #questions 9
 # create class for stack
class Stack:
  
    # create empty list
    def __init__(self):
        self.Elements = []
          
    # push() for insert an element
    def push(self, value):
        self.Elements.append(value)
        
    # pop() for remove an element
    def pop(self):
        return self.Elements.pop()
      
    # empty() check the stack is empty of not
    def empty(self):
        return self.Elements == []
      
    # show() display stack
    def show(self):
        for value in reversed(self.Elements):
            print(value)
  
# Insert_Bottom() insert value at bottom
def BottomInsert(s, value):
    
    # check the stack is empty or not
    if s.empty(): 
          
        # if stack is empty then call
        # push() method.
        s.push(value)
          
    # if stack is not empty then execute
    # else block
    else:
        popped = s.pop()
        BottomInsert(s, value)
        s.push(popped)
  
# Reverse() reverse the stack
def Reverse(s):
    if s.empty():
        pass
    else:
        popped = s.pop()
        Reverse(s)
        BottomInsert(s, popped)
  
  
# create object of stack class
stk = Stack()
  
stk.push(0)
stk.push(1)
stk.push(2)
stk.push(3)
stk.push(4)
  
print("Original Stack")
stk.show()
  
print("\nStack after Reversing")
Reverse(stk)
stk.show()


#question 10
# Python program to find smallest and second smallest elements
import math
 
def print2Smallest(arr):
 
    # There should be atleast two elements
    arr_size = len(arr)
    if arr_size < 2:
        print ("Invalid Input")
        return
 
    first = second = math.inf
    for i in range(0, arr_size):
 
        # If current element is smaller than first then
        # update both first and second
        if arr[i] < first:
            second = first
            first = arr[i]
 
        # If arr[i] is in between first and second then
        # update second
        elif (arr[i] < second and arr[i] != first):
            second = arr[i];
 
    if (second == math.inf):
        print ("No second smallest element")
    else:
        print ('The smallest element is',first,'and', \
              ' second smallest element is',second)
 
# Driver function to test above function
arr = [12, 13, 1, 10, 34, 1]
print2Smallest(arr)
