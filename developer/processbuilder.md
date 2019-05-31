
# Automate Simple Business Processes with Process Builder

  1. Process builder is a point and click tool that lets you easily automate if/then business processes and see a graphical representation of your process as you build 

  2. Every process consists of a trigger, at least one criteria node, and at least one action. You can configure immediate actions or schedule actions to be executed at a specific time.

  3. The trigger identifies when the process should run. For record change processes, the trigger determines which object and which of the following changes the process should pay attention to.

    * Trigger for a process examples 

      - Only when a record is created

      - Anytime a record is created or edited

  4. Criteria: Determine Whether or Not to Execute Actions 

    * While a process gets one trigger, you can add as many criteria nodes as your heart desires. 
    
    * Each criteria node controls whether or not the process executes the associated actions. If the record doesn’t meet the criteria, the process skips those actions and moves on to the next criteria node in the process.

    * In each criteria node, you can:

      - Set filter conditions.

      - Enter a custom formula. Like in validation rules, the formula must resolve to true or false.

      - Opt out of criteria and always execute the associated actions.
    
  5. Actions: What the Process Should Do

    * When a criteria node evaluates to true, the process executes the associated actions or waits to execute them at a scheduled time

      - Each immediate action is executed as soon as the criteria evaluates to true.

      - Each scheduled action is executed at the specified time, such as 10 days before the record’s close date or 2 days from now

  7. Process Types 

    * Record Change - A record is created or edited

    * Invocable - It’s called by another process

    * Platform Event - A platform event message is received

* Build a Process

  1. From Setup, enter Process Builder in the Quick Find box, select Process Builder, and then click New.

  2. Name the process Closed Won Opportunities.

  3. For the description, enter If a high-value opportunity is closed and won, create a draft contract and a follow-up task for the account owner.

  4. Configure the process to start when a record changes.

  5. Click Save.

# Add a Trigger

  1. Click Add Object.

  2. For Object, enter Opp to filter the list of options and select Opportunity.

  3. Select when a record is created or edited.

  4.  Choose Object and Specify When to Start the Process panel

  5. Click Save

# Add Criteria

  1. Click Add Criteria.

  2. Name the criteria Closed Won and High-Value.

  3. Leave Conditions are met selected.

  4. Check whether the opportunity has been closed and won.

    * For Field (1), choose Opportunity | Stage, and click Choose.

    * For Operator (2), leave Equals selected.

    * For Type (3), leave Picklist selected.

    * For Value (4), select Closed Won.

  5. With another condition, check whether the opportunity is high value.

    * Click Add Row.

    * For Field (1), choose Opportunity | Amount, and click Choose.

    * For Operator (2), select Greater than.

    * For Type (3), leave Currency selected.

    * For Value (4), enter 250,000.

  6. Click Advanced and select Yes.

    * When you select this option, the process ignores record changes that aren’t relevant to your defined criteria. For example, if the opportunity’s description is updated, the process won’t execute the associated actions.

  7. Click Save.

# Add a Schedule

  1. Under Scheduled Actions, click Set Schedule.

  2. Set the schedule for 6 days after the opportunity closes.

  3. Click Save.

# Scheduled Action

  1. Under the schedule we created earlier (6 Days After Close Date), click Add Action.

  2. For Action Type, select Create a Record.

  3. Name it Follow-up Task.

  4. For Record Type, select Task.

  5. Set the task's field values.

  6. Click Save 


