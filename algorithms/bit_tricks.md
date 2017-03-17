
## Bit Tricks 

- One of the most useful and effective low-level optimizations is bit manipulation, or using the bits of an integer to represent a set 
  Not only does it produce an order-of-magnitude improvement in both speed and size, it can often simplify code at the same time. 
  (A very good example of this is topcoder problem KiloManX solution with Dijkstra's algorithm)

- bit-wise versions of the operations are the same as with boolean, except that instead of interpreting their arguments as true or false, 
  they operate on each bit of the arguments. 
  for A=1010, B=1100, then
  ```
  A & B = 1000
  A | B = 1110
  A ^ B = 0110
  ~A = 11110101 (the number of 1′s depends on the type of A). 
  ```
- shift operators 
   a << b : shifts all the bits in a to the left by b positions, left-shifting by b is equivqlent to multiplication by 2^b.
   a >> b : shifts all the bits in a to the right by b positions, right-shifting as integer division by 2^b. 
  
- The most common use for shifting is to access a particular bit, for example, 1 << x is a binary number with bit x set and 
  the others clear (bits are counted from the right-most/least-significant bit numbered 0). 
  
- General use case: use an integer to represent a set on a domain of up to 32 values (or 64, using a 64-bit integer), 
 with a 1 bit representing a member that is present and a 0 bit one that is absent, you get these operations:
 ```
 Set union
 A | B
 
 Set intersection
 A & B
 
 Set subtraction
 A & ~B
 
 Set negation
 ALL_BITS ^ A
 
 Set bit
 A |= 1 << bit
 
 Clear bit
 A &= ~(1 << bit)
 
 Test bit
 (A & 1 << bit) != 0 
 ```
 
