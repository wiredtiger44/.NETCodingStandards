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

<a name="Magic"></a><a name="1.2"></a>
  - [1.2](#Magic) **No Magic Numbers and Strings**: Magic numbers or magic strings should be avoided if at all possible. A constant should be setup to represent the number or string.

    > Why? The meaning of a magic number or magic string can get lost over time. A constant is clearer and ensures that if a change needs to be made it happens in only one spot 

    ```code
    /* bad  */
    if (bnftPlanType == "Medical Plan")
    {
    }
    
    /* good */
    string benefitPlanTypeMedical = "Medical Plan";
    if (bnftPlanType == benefitPlanTypeMedical)
    {
    }
    ```


## Error Handling
<a name="swallowException"></a><a name="2.1"></a>
  - [2.1](#swallowException) **Don't Swallow Exceptions**: 

    > Why? Errors should either bubble up to a common error handling routine or be logged at the time of the error. In certain cases errors can be handled but those should be very narrowly specified.

    ```code
    /* bad (error is suppressed) */
    try
    {
        return ExportBenefitPlan(bnftPlanSK, planPgmCode);
    }
    catch (Exception ex)
    {
    }    
    
    /* good - error is bubbled up to higher level */
    return ExportBenefitPlan(bnftPlanSK, planPgmCode);
    ```

## Naming Conventions
<a name="Meaningful Names"></a><a name="3.1"></a>
  - [2.1](#meaningfulNames) **Meaningful Names**: 

    > Why? Meaningful names help other developers quickly look at the code and understand the functionality. 

    ```code
    /* bad - name is not meaningful */
    string mmm = "Medical Plan";
    
    /* good - name is representative of the variables representation */
    string benefitPlanTypeMedical = "Medical Plan";
    ```
