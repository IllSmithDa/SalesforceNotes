# Introduction to Global Variables and Visualforce Expressions

  1. Visualforce pages can display data retrieved from the database or web services, data that changes depending on who is logged on and viewing the page, and so on.

  2. This dynamic data is accessed in markup through the use of global variables, calculations, and properties made available by the page’s controller.

  3. Together these are described generally as Visualforce expressions. Use expressions for dynamic output or passing values into components by assigning them to attributes.

  4. A Visualforce expression is any set of literal values, variables, sub-expressions, or operators that can be resolved to a single value. Method calls aren’t allowed in expressions.

# Global Variables

  1. Open the Developer Console and click File | New | Visualforce Page to create a new Visualforce page. Enter UserStatus for the page name.

  2. In the editor, replace any markup with the following.

    * <apex:page>
        <apex:pageBlock title="User Status">
          <apex:pageBlockSection columns="1">
        	    
          </apex:pageBlockSection>
        </apex:pageBlock>
      </apex:page>
  
  3. Click Preview to open a preview of your page that you can look at while you make changes.

  4. Add the following markup between the <apex:pageBlockSection> tags.

  5. Add two more expressions that use the $User global variable to the markup for the User Status panel so that the page looks like the following.

    * <apex:page>
          
          <apex:pageBlock title="User Status">
              <apex:pageBlockSection columns="1">
                  
                  {! $User.FirstName } {! $User.LastName } 
                 ({! $User.Username })
                  
              </apex:pageBlockSection>
          </apex:pageBlock>
          
      </apex:page>

  6. The {! ... } tells Visualforce that whatever is within the braces is dynamic and written in the expression language. Its value is calculated and substituted at run time, when someone views the page.

  7. Visualforce expressions are case-insensitive, and spaces within the {! ... } are ignored. So these expressions all produce the same value: 

    * {! $User.FirstName}

    * {!$USER.FIRSTNAME}

    * {! $user.firstname }

# Formula Expressions - Visualforce lets you use more than just global variables in the expression language. It also supports formulas that let you manipulate values.

  1. In your UserStatus page, replace the separate expressions for the first and last name with the following formula expression.

    * {! $User.FirstName & ' ' & $User.LastName }

    * This expression combines the logged in user’s first name and last name, separating them with a space. The output should look identical.

  2. Add the following to the page markup, below the user information.

    * <p> Today's Date is {! TODAY() } </p>
      <p> Next week it will be {! TODAY() + 7 } </p>

      - These are more complex formulas that use the TODAY() function. Functions are built-in calculations that you can identify by the parenthesis after their name.

    * The first expression simply calculates the current date, and the second uses the addition operator to add seven days to the date. The output in your page will look something like this.

      - Today's Date is Thu Sep 18 00:00:00 GMT 2014
      Next week it will be Thu Sep 25 00:00:00 GMT 2014

  3. Add the following to the page markup, below the date expressions.

    * <p>The year today is {! YEAR(TODAY()) }</p>
      <p>Tomorrow will be day number  {! DAY(TODAY() + 1) }</p>
      <p>Let's find a maximum: {! MAX(1,2,3,4,5,6,5,4,3,2,1) } </p>
      <p>The square root of 49 is {! SQRT(49) }</p>
      <p>Is it true?  {! CONTAINS('salesforce.com', 'force.com') }</p>

      - Some functions, like TODAY(), have empty parenthesis, but some take parameters, values that you want the function to use to do its calculation. In this example, YEAR() takes a date parameter, which is provided by the TODAY() function, which takes no parameters. The MAX() function can take any number of parameters.

      - The CONTAINS() function is especially interesting. It returns a Boolean value: something that is either true or false. It compares two arguments of text and returns true if the first argument contains the second argument. If not, it returns false. In this case, the string “force.com” is contained within the string “salesforce.com”, so it returns true.

# Conditional Expressions

  1. Use a conditional expression to display different information based on the value of the expression.

    * For example, if an invoice has no line items, you might want to display the word “none” instead of an empty list. Or if an item has expired, you might want to display “Ended” instead of showing the ending date and time.

  2. You can do this in Visualforce by using a conditional formula expression, such as IF(). The IF() expression takes three arguments:

    * The first is a Boolean: something that is either true or false. For example, the CONTAINS() function, which you used earlier.

    * The second argument is the value that will be returned if the first parameter is true.

    * The third argument is the value that will be returned if the first parameter is false.

# Conditional Expressions Example 

  1. <p>{! IF( CONTAINS('salesforce.com','force.com'), 
        'Yep', 'Nope') }</p>
     <p>{! IF( DAY(TODAY()) < 15, 
       'Before the 15th', 'The 15th or after') }</p>

    * Before you save your changes and look at the results, try to predict what they will be! The results on your page will be something like this.

    * he first expression uses the same CONTAINS() function calculation as before. What’s different is that the IF() function converts the Boolean result of CONTAINS() into text more useful for displaying to the user. 
    
    * Similarly, the second expression shows one message during the first half of the month, and a different message the second half of the month.

  2. Delete all of your test expressions, leaving only the lines that use the $User global variable.

    * <apex:page>
        <apex:pageBlock title="User Status">
            <apex:pageBlockSection columns="1">

                {! $User.FirstName & ' ' & $User.LastName } 
               ({! $User.Username })
          
          </apex:pageBlockSection>
        </apex:pageBlock>
      </apex:page>
  
  3. Replace the line with the $User.Username expression with the following code.

    * ({! IF($User.isActive, $User.Username, 'inactive') })

      - isActive is another field available on the $User global variable. It’s a Boolean field that’s true if the user is active, and false if they’ve been deactivated. Now the User Status panel will show the user’s username if they’re active, and “inactive” if they’re not.

# More on Global variables 

  1. There are nearly two dozen global variables that can be used within Visualforce. They’re useful for getting information about the currently logged in user, as you saw, but also for getting details about the organization ($Organization), settings ($Setup), details about custom objects ($ObjectType), actions available on those objects ($Action), and so on. See the Visualforce global variables reference to dive in.

  2. Similarly, there are dozens of functions that can be used in Visualforce. The list is similar to, but not quite the same, as the functions available in formula fields. Where they overlap the functions behave the same, so you can reuse most of what you know about formula fields when you write Visualforce expressions. See the Visualforce functions reference for a complete list.