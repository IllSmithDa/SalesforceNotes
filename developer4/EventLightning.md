# Custom Events

  1. WHen you have multiple components and they need to communicate with each other 

  2. When one component 1 does something, another component 2 should subscribe to that original component 1 and component 2 updates itself based on component 1. 

    * Component 1 is independent component while component 2 is dependent component - dependent on component 1. 

  3. Child components are imbedded into a parent component. 

  4. Component events are handled by the component itself or a component that instantiates or contains the component.

  5. Application events are handled by all components that are listening to the event. These events are essentially a traditional publish-subscribe model.
 
# Lightning Events 

  1. Parent to Child 

    * Parent is the Publisher 

    * Child is the handler

  2. Publisher and Handler

    * publisher is the component whose actions initializes the event. 

    * Handler is the component that responds to the Publisher and the effect of the cause and effect. Handler is subscribed to the publisher which listens for a publisher event initialization.

# Event Bus

  1. There can be many events going on and so it creates a event bus. 

  2. WHen publisher initalizes event, there are usually many subscribers and so it is good to refresh event to prevent it from failing. 

  3. If you want multiple every parent to listen and handle the event, you have to set bubbles to true. If Bubbles is false, then only the direcly parent will be able to access the child. 

# Pub Sub Model

  1. For handling events between two components that are not related at all in a heirarchilcal sense

  2. Pub sub component and file must be copied from a git hub link

  3. 
  
