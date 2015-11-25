#Axioms
Infinite register machine  
Minimal instruction set (4 or so instructions)  
Church data representation  
Intensional equality of AST  

#Optimization

How do we optimize register operations on a real machine, which has fast arithmetic operators? 
We need to expand the instruction set beyond lambda calculus.  
We need to support native data representations (such as numbers).  

3 can be represented in registers as:  
R1 -> R2 -> R3 -> 0 (church numeric expression)  
R1 -> 3 (arithmetic expression)  

Our optimizer must be able to convert from a church numeric expression to an arithmetic expression when appropriate. To do this, we use sum types (also known as variants).  

In the optimizer, we override the concept of equality to be extensional with regards to optimized types.  

The sum type for numbers would be (NumberRepresentation, Value). The sumtype would carry a conversion method between "church numeric expression" and "arithmetic expression"  

Two number expressions would be equal if they possess extensional equality  

#References
https://en.wikipedia.org/wiki/Counter_machine_models  
https://en.wikipedia.org/wiki/Church_encoding  
https://en.wikipedia.org/wiki/Extensionality  
