# .NET Coding Standards
Coding standards for .NET development

## Table of Contents
1. [Functionality](#functionality)
2. [Error Handling](#error-handling)
3. [Naming Conventions](#Naming-Conventions)
4. [Code Styling](#Code-Styling)


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
  - [2.1](#swallowException) **Don't Swallow Exceptions**: Don't swallow exceptions without handling or logging them.

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
  - [3.1](#meaningfulNames) **Meaningful Names**: Use meaningful Names to describe constants, variables, and methods.

    > Why? Meaningful names help other developers quickly look at the code and understand the functionality. 

    ```code
    /* bad - name is not meaningful */
    string mmm = "Medical Plan";
    
    /* good - name is representative of the variables representation */
    string benefitPlanTypeMedical = "Medical Plan";
    ```

## Code Styling
<a name="NoDebuggerStatements"></a><a name="4.1"></a>
  - [4.1](#NoDebuggerStatements) **No Debugger Statements**: Debugger statements should not be checked in. Use them temporarily and sparingly to track down problems.

    > Why? Debugger statements can cause an application to behave differently in development versus testing.

<a name="NoCommentedCode"></a><a name="4.2"></a>
  - [4.2](#NoCommentedCode) **No Commented Code**: Commented code should not be checked in. 

    > Why? Commented code can be confusing. History of code is kept in source control so commented code is not necessary.

    ```code
    /* bad - a bunch of commented code */
    //string mmm = "Medical Plan";
    //int mmm = 1;
    
    string benefitPlanTypeMedical = "Medical Plan";
    //if (mmm == "Medical plan");
    //if (mmm == 1);
    if (bnftPlanType == benefitPlanTypeMedical)
    {
    }
    
    /* good - name is representative of the variables representation */
    string benefitPlanTypeMedical = "Medical Plan";
    if (bnftPlanType == benefitPlanTypeMedical)
    {
    }
    ```
