# How to rollout lightning experience

  1. It takes a team to rollout on a Salesforce project

    * Identify key stakeholders at your company from all affected departments

  2. Revisit your process and make sure if check if a process could be done more efficiently

  3. Perform a Gap Analysis

    * Performing a gap analysis is where you get into the nitty gritty details of how your current Salesforce implementation will work when you move to Lightning Experience. Access the Readiness Check from the Lightning Experience Transition Assistant. 

    * From Setup in Salesforce Classic, click Get Started in the Lightning Experience Transition Assistant tile at the top of the menu (1).

    * Select the Discover phase (2).

    * Click Evaluate Lightning Experience Benefits and Readiness to expand the stage (3).

    * Click Check Readiness next to Check your Lightning Experience readiness (4).

    * After you kick off the Readiness Check, Salesforce generates a PDF Readiness Report and emails it to you. Salesforce also saves the report to Salesforce Files.

  4. Improve Your Implementation with Salesforce Optimizer

    * The tool identifies things you can simplify, improve, or leave behind when transitioning to Lightning Experience—so you know where to concentrate your time and resources.

    * Some of the features that Optimizer evaluates include Apex triggers, fields, profiles, record types, and validation rules. 

    * The Optimizer report identifies page layouts that aren’t being used in your implementation, so you can delete them before you transition to Lightning Experience.

    * The Optimizer report tracks down any hard-coded URLs that are lurking in your org and flags them for you. Hard-coded links in your implementation will likely break in Lightning Experience.

    * Older web browsers aren’t supported by Lightning Experience. The Optimizer report lists users who access Salesforce from unsupported browsers so you can help them update to a supported version.

    * Lightning Experience includes many productivity-enhancing features that aren’t available in Salesforce Classic. The Optimizer report recommends Lightning Experience-only features that your users may benefit from, such as the Lightning Sales or Service Consoles.

    * To Launch the optimizer

      - Fromm Setup, enter Optimizer in the Quick Find box, then select Optimizer.

      - Click Launch | Allow.

  5. Use the Preview tool that’s available from the Lightning Experience Transition Assistant. Preview lets you explore your production org in Lightning Experience without actually enabling the new interface

  6. If you have a sandbox, that’s the ideal place to enable the new interface and play around with settings and customizations in earnest.

  7. Assess the impact 

    * You can use several methodologies when assessing impact, including assigning a numeric value to each gap, or plotting the gaps on a simple chart.

  8. Educate Your Company About Lightning Experience

    * So start your presentation by showcasing the benefits of Lightning Experience.

    * If you’re an existing Salesforce customer, explain if any features that are important to your company aren’t available in Lightning Experience today.

# Rollout Plan

  1. Unless your org is small, it can be advantageous to transition your users to Lightning Experience over the course of several phases. 

    * This approach allows you to tackle your business and technical requirements incrementally, and iterate on lessons learned. For each phase, pick teams or groups of users whose business needs are met by the current state of your Lightning Experience implementation.

    * After launching a phase, collect feedback. Then fine-tune things and kick off the next phase.

  2. Org-Wide Rollout

    * With all your users moving to Lightning Experience at the same time, you can run a single campaign to get everyone on board. And you only need to maintain training materials for one interface.

    * We’re continually improving and enhancing Lightning Experience. The longer it takes to move your org over, the more features and opportunities for improved productivity you’ll get behind on.

  3. Unleash the Power of Super Users

    * Super users are also the first people your employees go to for help, and they can be incredible in helping you answer questions and provide support.

    * Super users are often natural leaders, well-respected by their peers, and can be your evangelists in the field. And when it comes to rolling out Lightning Experience, they can help make your project a success.

  4. Create a Chatter Group for the Rollout Team

    * Using Chatter, you can share files, collaborate in context, and share relevant updates with the whole team.

  5. Pick launch date wisely when key stakeholders are available

  6. Create a Project Schedule

  7. Define measure for success

    * For example, you could look for productivity gains, data quality gains, or financial goals, such as:

      - 20% reduction in opportunities with no follow-up tasks
      
      - 15% increase in calls logged

      - 5% increase in lead conversion rate

  8. Create a Marketing and Communication Strategy
 
    * Create a topic in Chatter for all your communication updates to drive momentum and buzz.

  9. Create a Training Plan

  10. Test Your Customizations and Iterate

    * For existing customers, if you already have customizations in place, we recommend enabling Lightning Experience in a sandbox and testing their behavior.

    * For unsupported features, like JavaScript buttons, analyze what the underlying function is of each. Here’s a set of questions you can use in your analysis:

    * Here’s a set of questions you can use in your analysis:

      - What does the customized feature do?

      - What objects are affected or accessed?

      - What are the resulting actions of using the customized feature?

      - What is the user experience?

      - Where can your user access the customized feature?

# Going Live

  1. Depending on the project, the go-live step can be simple, complex, or somewhere in between. We make it easier with the Lightning Experience Transition Assistant, where you can access all the steps that need to be completed to move to Lightning Experience.

  2. Access this page from Setup in Salesforce Classic, by clicking Get Started in the Transition Assistant tile.

  3. Drive Adoption by Optimizing Your Implementation

    * optimize your rollout by measuring how things are going and iterating on all the good work you’ve done so far.

    * Monitor how your success metrics are looking. For example, collect feedback on how users are liking the new experience. And measure for things like productivity gains, business success, and adoption rates—including how many users are switching back to Salesforce Classic and why.

  4. Engage with Super Users

  5. Measure Results

    * When you were planning your rollout strategy, you worked with your executive sponsor and stakeholders to determine your success metrics. Those metrics might have included things like:

      - 20% reduction in opportunities with no follow-up tasks, 15% increase in calls logged, 5% increase in lead conversion

      - Employee satisfaction

  6. Survey Your Users

  7. Use Reports and Dashboards in Salesforce

    * If you’ve decided to use Salesforce metrics for your success measures, then you can create reports and dashboards within Salesforce to track those metrics.

  8. Deliver an Executive Summary
