# Chatter Basics

  1. Salesforce real time collaboration application that lets your users work together, talk to each other and share information

  2. lets users collaborate on sales opportunities, service cases, campaigns and projects embedded apps and custom actions. 

  3. available on mobile

  4. you can follow people, groups, and create groups

  5. also contains a search engine to find people, groups, teams, work records, etc

# Profiles 

  1. Everyone in a organization has a chatter profile customizable with a photo, contact information, personal overview and so on

  2. Click the person’s name on the hover card to navigate to their full profile.

  3. Other ways to get to a person's profile

    * Search the person’s name using the global search field at the top of Salesforce.

    * Click the People tab and find the person in a list of everyone you can see in Chatter. If you don’t see the People tab, try the overflow menu. If you don’t see the People option there, you can use the App Launcher to get to the People tab.

    * In the App Launcher, search for People, click People in your results, and then click the person’s name on the People list.
  
# Groups
  1. they are the main collaboration space in Chatter

  2. You can organize a group around a project and add all project participants to it.

  3. Groups help users build, preserve, and share knowledge that’s vital to getting the job done and keeping everyone aligned.
  
  4. There are many types of groups including

    * public groups - visible and open to all employees (anyone can join)

    * private groups - only open to group members, request are made to join group and only group members can post, comment and add files

      - still see picture and discription but not feed or files 
    
    * unlisted groups - do not appear in searches and hidden outside of group members. group owner must send out invites

    * groups with customers - private or unlisted groups that allow external users like customers to join. Group owner must send invite

    * broadcast only - groups only allow owners and managers to create posts. groups members can still make comments 
 
  3. You can follow people and records, which allow you to see updated from those people and records
  
  4. You can categorize posts using topics

    * topics give users a way to add searchable terms to their feed post. 

    * great for adding to an ongoing discussion

    * fastest way to add a topic is using a hastag

      - e.g #GroupMeeting

# Making Groups 

  1. Skip to step 5 if groups enabled. In the Setup Quick Find box, enter Chatter Settings, click Chatter Settings, and then click Edit.

  2. Allow Records in Groups (1) is likely selected by default; if it isn’t, select it.

  3. Select to enable unlisted groups (2).

  4. Click Save

  5. In Salesforce, click the Groups tab. If you don’t see it, open the App Launcher, search for Groups, and click your result

  6. On the Groups list page, click New to open the New Group modal.

  7. Fill out info and save 

    * Name - group name

    * Description - group description

    * Information - provide any group details you care to share, and format your details using rich text editor controls.

    * Owner - Assign someone to be group owner. Start entering a name and choose from the resulting list. You can always leave it as-is and own the group yourself.

    * Member count - populates after you create the group.

    * Record Type - shows the type of feed you chose (Post or Question) in step 3.

    * Archive - With the right role or permission, you can edit a group and mark it for Archive here. By default, groups are archived after 90 inactive days. To prevent automatic archiving, select Disable automatic archiving.

      - When a Chatter group is archived, group members can’t post messages or share files with the group.
    
    * Access type - who can access the group 

    * Allow customers - can customers join this group?

    * Broadcast only - is this a broadcast only group?

# Feedtracking

  1. Feed tracking in Salesforce highlights changes to records by automatically announcing them in the record’s feed. 

  2. With all this activity, how do you stay on top of what’s going on? Another feature, in-app notifications, lets you know when the things you follow change.

  3. Default fields that are tracked: 

    * Account: Account Name, Account Owner

    * Case: Case Owner, Priority

    * Group: Allow Customers, Description, Access Type, Information, Information Title, Name, Owner

    * Contact: Account Name, Contact Owner, Name

    * Lead: Lead Owner, Lead Status, Name

    * Opportunity: Amount, Close Date, Opportunity Name, Opportunity Owner, Stage

    * User: About Me, Address, Email, Manager, Phone, Title

# Enable and Customize Feed Tracking

  1. From Setup, enter Feed Tracking in the Quick Find box, and then click Feed Tracking.

  2. From the list of objects, select Contact.

  3. Select Enable Feed Tracking.

    * If Enable Feed Tracking is already selected in your Trailhead Playground, it saves you a step. Feed tracking isn’t enabled by default for all objects. So remember to take this step when you’re setting up your own feed tracking.

  4. Select up to 20 fields to track.

  5. Click Save

# Chatter Tab

  1. What I Follow - combines all the feeds from the people, records, and groups the user follows.

  2. To Me - combines all the feeds where the user is mentioned.

  3. Bookmarked - combines all the posts the user has bookmarked.

  4. Company Highlights - uses the Einstein aritificial intelligence algorithmn to pull out posts likely to be interesting to the user

  5. My Drafts - shows posts the user hasn't published yet 

# Streams 

  1. Streams let your users combine all kinds of feeds into one stream for easy access. 

    * For example, add the profiles of everyone up your management chain to keep an eye on what they’re up to.

    * Add the record feeds from a current project to a stream to cut down on the bouncing around you must do to get the full picture.

    * The Recent Groups section provides quick navigation to the five groups you last visited and a fast way to create a group.

# Following 

  1. With it, you and your users can follow people and get notified when they’re active in Chatter.

  2. People can follow each other, independent of their teams, boosting collaboration across functional borders. 

  3. People can follow groups and records, too. Following is a great way to get notified about the people and things you and your users are interested in.

# Chatter Search

  1. There are two types of searches available to Chatter users. 

    * Global search (1) searches the entire org and returns only the results the user has access to. With global search, users can limit their searches to the type of object they want to find.

    * Feed search (2) lets users look for results from the current feed. Feed search offers a great way to find that vital bit of information buried in an active thread.

# Actions

  1. Adds functionality like post, poll and questions to the chatter publisher with fewer clicks
  
  2. Types of Actions

    * Standard actions - actions that are automatically included when Chatter is enabled such as Post, Link, File etc

    * Nonstandard actions - actions you create and customize yourself

    * Default actions - Salesforce predefined actions

    * Mobile smart actions - set of preconfigured acitons and supported on the same list of objects
    
    * custom actions - lightning components, visual force pages or canvas apps that you define

      - custom actions allowing users to write comment with more than 5000 characters

    * productivity actions - Actions defined by salesforce and attach to limited set of objects

      - cannot be deleted or edited in any way

# Add actions to Group Layout 

  1. In the Setup Quick Find box, enter Group, and then click Group Layouts.
  
  2. On the Group Layout row, click Edit.

  3. In the Group Layout panel at the top of the page, select Mobile & Lightning Actions. If it’s not already there, drag New Case to the Salesforce Mobile and Lightning Experience Actions area.

  4. Under Group Layout at the top of the page, click Save

  5. There’s the New Case action on the group page.

# Add and Promote Members 

  1. To add more members, go to Groups tab, open the actions menu in the group banner, and select Manage Members. 

    * In the Add Members dialog, search for the people you want to add and click Add next to their names.

  2. You can also search for existing members and promote them to manager. Group managers enjoy the same rights and privileges as the group owner. 

    * To promote a member to manager:

      - Open the Add Members dialog.

      - Search for an existing member.

      - Select Manager from the menu next to their name.

# Enable Chatter Email Notifications

  1. When you enable email notifications for Chatter, your users start receiving email notifications about new posts, comments, and other changes.

  2. Enable email notifications for all users in Setup, on the Chatter Email Settings page.

    * In the Setup Quick Find box, enter Email Settings, and then click Email Settings.

      - Allow Emails to turn on Chatter email notifications for all your users.

      - Allow Email Replies to allow users to post their replies to email notifications in Chatter.

      - Allow Posts via Email to allow users to post to groups through email.

      - Allow Attachments via Email to allow users to include attachments when they use email to post to a group.

      - Show mobile app download badges to add App Store and Google Play badges for the Salesforce app to all Chatter email notifications from your internal org.

# Chatter Settings 

  1. To get to Chatter Settings, from Setup enter Chatter in the Quick Find box, and click Chatter Settings.

  2. Chatter Settings - Turns Chatter on or off for your org.

  3. Groups - Provides options for your Chatter groups. Controls whether archiving is enabled, whether you can associate records with groups, and whether unlisted groups are allowed in your org.

  4. Draft Posts - Adds the My Drafts feed to the Chatter tab. Every seven seconds, saves posts that users are drafting and makes them available in the My Drafts feed. When the user posts the entry, the draft is automatically removed from the My Drafts feed.

  5. Rich Link Previews in Feed - Converts links in posts into embedded videos, images, and article previews. Larger images are truncated with a More link that lets your users see the full preview.

  6. Emoticons in Feed - Converts keyboard characters into emoticons, so these keyboard characters :) become this emoticon Smily emoticon.

  7. Out of Office - 	Adds a control to user profile pages for setting a personal out-of-office message.

  8. Topics - Allows authenticated and guest users to view topics in Salesforce Sites and portals.

  9. Approval Posts - Allows requests for approval to appear in a user’s feed as a post.

  10. Coworker Invitations - Allows licensed Salesforce users to invite unlicensed coworkers to Chatter. Users who accept invitations see only profiles, files, and groups. They can't see any object details unless you grant them a full Salesforce license.

  11. Customer Invitations - Allows licensed users to invite customers to private groups that the licensed user owns or manages. Licensed users can invite customers who are from outside your email domains. Invited customers can see information only in the groups they're invited to. They can interact only with members of those groups.

  12. Actions in the Publisher - Actions in the Publisher is a legacy setting that has no application in Lightning Experience. 

  13. Recommendations in the Feed - Allows the posting of recommendations for using the Salesforce Today app in your users’ feeds. 

  14. Post and Comment Modification - Lets certain users edit feed posts and comments. Affected users include the author, the person who owns the record that was posted or commented on, and the Chatter or community moderator.

  15. Rich Text Posts - Makes the editor in the Chatter publisher a rich text editor. The rich text editor supports text formats, inline images, hyperlinks, and, when enabled for the org, code snippets.

  16. Pin Posts in Feeds - Make post pinning available to your communities and your internal org. First make the feature available through this setting, then assign permission to pin through profiles or permission sets. When the permission is assigned, users can pin up to three posts to the top of the topic and group feeds that they have access to.

# Approvals in Chatter 

  1. Approval processes define the steps to take to approve a record in Salesforce and identify the person who provides approval at each step.

  2. You can configure the approval process to send out an approval request as a Chatter post.

# Chatter Rollout Strategy

  1. It is critical to develop a Chatter rollout strategy
 
  2. Identify key people to be Chatter champions

    * Executive Sponsor - This person must believe in the power of social collaboration and Chatter. They must be willing to invest time to make Chatter collaboration a success

    * Evangelist - people at your company who have incredible knowledge and already love social collaboration. Your evangelists can help answer questions, encourage other users who are nervous about posting, create and manage groups, and curate content.

    * Community Manager - You need a Community Manager curating quality content and driving user engagement. Examples of great content include helpful files, links to industry news articles or videos, and posts about events or exciting announcements at your company. 
 
  3. A great Chatter rollout needs a solid communication plan. 

    * Create marketing content - ou can send drip emails and videos to advertise that Chatter is coming. Consider allocating budget for fun swag or a launch party with cake and balloons

    * Create a schedule - Choose your launch date carefully. Avoid busy times for your company (for example, the last day of the sales month) and holidays. It’s a general best practice to turn on Chatter after hours. Once you’ve decided on your launch date, create a schedule for your pre-launch communication.

  3. Chat ettiquite - Consider putting together a simple list of guidelines for user behavior. Publish the list and share it with your users. Post it in a public place, like an All Company Chatter group.