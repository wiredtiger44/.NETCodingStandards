# .NET Coding Standards
Coding standards for .NET development

## Table of Contents
1. [Functionality](#functionality)
1. [Error Handling](#error-handling)
1. [Naming Conventions](#Naming-Conventions)

## Functionality
<a name="Re--implementation"></a><a name="1.1"></a>
  - [1.1](#Re--implementation) **Re-implementation**: Is this functionality already implemented somewhere else? Is there something similar that can be modified?

    > Why? One set of code is easier to maintain. 

<a name="Re--implementation"></a><a name="1.1"></a>
  - [1.1](#Re--implementation) **Re-implementation**: No magic numbers or magic strings

    > Why? One set of code is easier to maintain. 




## Error Handling
<a name="swallowException"></a><a name="2.1"></a>
  - [2.1](#swallowException) **Don't Swallow Exceptions**: 

    > Why? NO-ERROR suppresses errors, which can cause database inconsistency issues, memory leaks, infinite loops and more...

    ```openedge
    /* bad (error is suppressed, cMemberName is never assigned */
    ASSIGN iMemberNumber = INTEGER("ABC")
           cMemberName   = 'ABC' NO-ERROR.
        
    /* good (ver 1) - using structured error handling */
    ASSIGN iMemberNumber = INTEGER("ABC")
           cMemberName   = 'ABC'.
    /* ... some code... */
    CATCH eExc AS Progress.Lang.ProError:
      MESSAGE "Error:" + eExc:GetMessage(1).
    END.
        
    /* good (ver 2) - classic error handling (split safe assignment from unsafe) */
    ASSIGN cMemberName   = 'ABC'.
    ASSIGN iMemberNumber = INTEGER("ABC") NO-ERROR.
    IF ERROR-STATUS:ERROR THEN
      DO:
        /* handle error here */
      END.
    ```

## Naming Conventions
<a name="Meaningful Names"></a><a name="3.1"></a>
  - [2.1](#meaningfulNames) **Meaningful Names**: 

    > Why? Meaningful names help other developers quickly look at the code and understand the functionality. 

    ```openedge
    /* bad (error is suppressed, cMemberName is never assigned */
    
    /* good (ver 1) - using structured error handling */
        
    
    ```
