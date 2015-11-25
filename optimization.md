language should target an infinite register machine with minimal instructions    
no arithmetic, use church numerals  

equality at the lowest level of the language is intensional - ie, two objects are equal if they have the exact same AST representation  

This poses a problem when we want to optimize register operations on a real machine, which has fast arithmetic operators  

We need to be able to support alternate representations of objects (such as numbers)  

3 can be represented in registers as:  
R1 -> R2 -> R2 -> 0 (church numeric expression)  
R1 -> 3 (arithmetic expression)  

Our optimizer must be able to convert from a church numeric expression to an arithmetic expression when appropriate  

To do this, we use sum types (also known as variants)  

In the optimizer, we override the concept of equality to be extensional with regards to optimized types  

The sum type for numbers would be (NumberRepresentation, Value). The sumtype would carry a conversion method between "church numeric expression" and "arithmetic expression"  

two number expressions would be equal if they possess extensional equality
