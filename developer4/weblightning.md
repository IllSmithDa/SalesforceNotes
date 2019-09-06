# enque.action

  1. When there are multiple actions and callbacks, this function will help order your actions 

  2. lightning and aura framework, these are heavy components. Your web browser only understand Javascript, CSS, HTML. 

    * Everything else has to be broken down to these components

    * Aura has alot of very heavy components and takes time to load

# Features now available which was not available before

  1. Templates - new HTML tags like phone which was not there before 

  2. rendering optimization - partial rendering without refreshing entire webpage 

  3. security, lightning data service and base lightning components are all that is controlled by the framework itself including LWC. 

    * The rest is controlled by the web standard itself. 

# Main advantages of LWC

  1. Reusable components for this framework and other frameworks is a big advantages

  2. simpler components in HTML

  3. Follows the ECMA web standards

    * It has less server side load and more on the client side 

    * automatically get better performance, as less stuff processed by server

    * more security as less data is moving from client to server

# Salesforce development 

  1. Dev Box

  2. AT (acceptance testing) Sandbox

    * integration testing 

    * Test from individuals

  3. UAT (Sandbox)

    * Testing with large groups of users 

  4. Production

    * migration into Production

  5. For every step, there will be a main feature branch which will contain multiple child branch.

    * you can create local branch and make a pull request

    * Ant, Bamboo, AutoRabbit, Copado are all used which follows the branch model

    * So you just create a new branch for every step rather than using the org to move code from Dev Box to Production

    * THe master branch is the working production code which can be used to create a new org 

    * Branches help resolve code conflicts thanks to the pull requests. 

    * This is the continuous development pipeline

# Salesforce DX

  1. It is the lCW pipeline 

  2. For each developer, it creates a a scratch org which replicates your org 

    * It is a virtual clone of a dev box - a small copy of your org for the purpose of unit testing

    * Each developer get their own clone which will get pushed to a child branch.

    * Each child branch will make a pull request to the parent branch with a designated approver

    * Unit testing and code compilation has been done separately and sent to parent branch

    * scratch org prevents having to buy orgs just for the sake of development

    * Dx is a set of tools that allow you to connect your code to your org 

  3. 