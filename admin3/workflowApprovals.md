# Workflows and Approvals

  1. You create a case such as problem with your laptop. After no one responds after 4 hours, you want to send reminder or escalate the case to the next level 

    * Approval - short term leave, long term leave, loan mortgage

    * parallel Approval - all departments have to approve 

    * You need approval for a 20 percent discuont

    * You may have a new policy, progra or project that requires approval from all the different deparments


  2. Go to Setup, Workflow Rules, and set up object and workflow rules there 

    * created option - salesforce evalulate the rule a new record is created in the object

    * update option - salesforce evaluates the workflow rule when record is created and edited 

    * criteria based - you can also set workflow rule based on criteria is met

      - good for when you want criteria is primary source of when workflow rule is evaluated 

    * Timed based workflow actions 

      - good for time sensitive actions you want to add 

    * You can add classic email template and email alerts as well as outbound messages both through setups

# Workflow Order !

  1. Field Update always go first 

  2. Then Tasks 

  3. Then Email alert

  4. Outbound message is always last

# Outbound Message 

  1. You need to create a endpoint url for your outbound message 

    * For example, https://requestbin.com/



# Parent Child and workflow

  1. Is it possible to access and perform record updates from child records through the parent record and vice versa

    * If you define workflow in the master, it is not possible to access the child records

    * You can however, access the parent records from the child 

# Parallel Approvals

  1. All departments must approve or the overall approval will be rejected 

  2. You first need a entry criteria

  3. You need a action to take based on whether approval is accepted and rejected

  4. Set up whether you can reroll or resubmit an approval. Or edit a approval 

  5. Approvers should have access to the record that is being submitted for approval - with at least read level access. 

  6. Note that you should review seurity settings before you start creating approval processes

# Configure Approval Process

  1. In Setup, go Approval Processes, select object and follow steps.

  2. Select the approver which often can be a manager, or a assignment queue or automatically assign it to a particular user

    * Fourth option you can add multiple roles, queues, users 

  3. You can also add a final approval action when request have been approved and final rejection aciton when request has been ultimately rejected. 

    * Can be found in the Approval Processes Settings 

    * Actions can include sending email alert, updating fields like user status. 

    * You can also add a Recall option in case you want to add option for approval to be resubmitted 

  4. The moment a request for approval is made, the record is then locked until approver accepts or rejects the approval

    * When record is locked, you are not allowed to edit the record

  5. Unanimous approval means it must be approved at every step of the approval processes. 

  6. Only the owner of the record can submit the record for approval. Otherwise approval will not go through

  7. Entry criteria and record ownership both are reasons why an approval can go or can't go through

    * System admin can always submit despite not being the record owner 

# Process Builder 

  1. Process build automates process depending on what criterias have been met. 

  2. Merge field value

    * the field within a Object that you are referring to you. 

    * can be both standard and custom object and fields

    * Unlike workflow, which only has 4 actions, process builder have up to 11 different actions varying from sending email alerts to sending a post on chatter. 

    * You can even do timed dependent and time sensitive actions using process builder which you can also do on the workflow setup. 

  3. Lightning process builder allows parent objects to access child objects and vice versa

# Order of Execution

  1. Salesforce runs system validation to check the record for:

    * Compliance with layout-specific rules
 
    * Required values at the layout level and field-definition level

    * Valid field formats

    * Maximum field length

  2. Runs most system validation steps again, such as verifying that all required fields have a non-null value, and runs any user-defined validation rules.

  3. Executes duplicate rules

  4. Saves the record to the database, but doesn't commit yet.

  5. Executes assignment rules.
  
  6. Executes auto-response rules.

  7. Executes workflow rules.

  8. If there are workflow field updates, updates the record again.

  9. Executes processes and flows launched via processes and flow trigger workflow actions.

  10. Executes escalation rules.
