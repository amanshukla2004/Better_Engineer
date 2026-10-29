read : abstract class


## why this code implementation is not good 
 upi payment is only supported by RupayCreditCard
 but in the abstract class of CreditCard we have added the upiPayment method as we are forced to add this method in the abstract class of CreditCard
 so every class of CreditCard will have to implement this method but this is not the case


### solution 1 :
remove 
        public abstract void upiPayment(); 
from the abstract class of CreditCard and add it to the RupayCreditCard class.

problem after solution 1: 
but someday we get a new requirement from the business that now the visa credit card also supports the upi payment


also Diners Credit card does not support refund 

international payments is not supported by rupay but supported by all other

so much of code duplication will be there 

What this problem id called :

# Interface Segregation Principle 

it states that code should not be forced to use methods it doesnot need.
it states that if any particular child isnot intended to be having a particular behaviour of the parent then it should not be forced to have that behaviour .