# .NET Coding Standards
Coding standards for .NET development

## Table of Contents
1. [Functionality](#functionality)
2. [Error Handling](#error-handling)
3. [Naming Conventions](#naming-conventions)
4. [Code Styling](#code-styling)


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
 <a name="Single character variables"></a><a name="3.2"></a>
  - [3.2](#singlecharacter) **No Single Character Variables**: Use meaningful Names to describe variables. Use of one character variables should be limited to loops

    > Why? Meaningful names help other developers quickly look at the code and understand the functionality. 

    ```code
    /* bad - name is not meaningful */
    string m="Medical plan";
    
    /* good - name is representative of the variables representation */
    string benefitPlanTypeMedical = "Medical Plan";
    
    /* good - single character used in loop */
    for (int i = 0; i < length; i++)
    {
        
    }
    ```

<a name="Class names"></a><a name="3.3"></a>
  - [3.3](#ClassNames) **Class Names**: Class names should use pascal casing. Class Names should be nouns. 

    > Why? Standardizing class names helps differentiate them from other types of objects. 

    ```code
    /* bad - name is not Pascal case and is a verb */
    public class exportingdownloading
    
    /* good - name is Pascal case and is a noun */
    public class BenefitPlan
    ```
    
    <a name="Method names"></a><a name="3.4"></a>
  - [3.4](#methodNames) **Method Names**: Use Pascal casing for Method Names.  Method names should start with a verb and tell what it does. 

    > Why? Standardizing method names helps differentiate them from other types of objects. 

    ```code
    /* bad - name is not Pascal case and does not start with verb */
    public string benefitPlan(long benefitPlanSK)
    {
    }
    
    /* good - name is Pascal case and start with verb */
    public string GetBenefitPlan(long benefitPlanSK)
    {
    }
    ```
    
      <a name="Variable and Parameter names"></a><a name="3.5"></a>
  - [3.5](#VariableParameterNames) **Variable and Parameter Names**: Use Lower Camel casing for variables and method parameters.  

    > Why? Standardizing method names helps differentiate them from other types of objects. 

    ```code
    /* bad - name is not Camel case */
    public string benefitPlan(long benefitplansk)
    {
      string benefitplantype;
    }
    
    /* good - name is Camel case */
    public string GetBenefitPlan(long benefitPlanSK)
    {
      string benefitPlanType;
    }
    ```
    
      <a name="Interface names"></a><a name="3.6"></a>
  - [3.6](#interfaceNames) **Interface Names**: Use Pascal casing for Interface Names and begin with an "I" Prefix. Interface names should be nouns.

    > Why? Standardizing method names helps differentiate them from other types of objects. 

    ```code
    /* bad - name is not Pascal case, does not start with "I", and is not a noun */
    public interface processing
    {
    }
    
    /* good - name is Pascal case , starts with an "I", and is a noun */
    public interface IBenefitPlan
    {
    }
    ```
    <a name="Boolean/Bit varialbes"></a><a name="3.7"></a>
  - [3.7](#VariableParameterNames) **Boolean/Bit Variable Names**: Use Lower Camel casing for variables and method parameters. Prefix with "is" or similar.

    > Why? Standardizing method names helps differentiate them from other types of objects. The "is" prefix makes it clear what value is true and what value is false.

    ```code
    /* bad - name is not lower Camel case and is not prefixed with "is" or similar */
    bool family;
    
    
    /* good - name is lower Camel case and is prefixed with "is" or similar */
    bool isMemberOfFamily;
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
