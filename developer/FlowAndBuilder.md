# When the Process Builder is not enough 

  1. Process Builder isn’t designed to address every possible use case, so you may find that it can automate parts of your business process, but not all. For example, Process Builder can’t:

    * Post to a community feed.

    * Submit a related record for approval.

    * Delete records

    * Create a bunch of records and associate them with each other.

    * Perform complex logic

    * Clone a process

  2. If we can't do something in Process builder, we can do it in Flow instead 

    * You've been asked to automatically create renewal opportunities when an opportunity is Closed Won. The renewal should be a clone of the original opportunity. We can clone records in Process Builder, but we also need to clone the products and associate them with the renewal opportunity.

    * In Process Builder, you can’t grab the ID of the created record and use it elsewhere. Luckily, you can do that in a flow. Just build a flow that clones the opportunity and its products, and build a process that calls the flow when an opportunity is closed won.

