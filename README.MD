This project demonstrates the difference between a JS event.target and event.currentTarget

event.target: the element on which the event occurred. If you add an 'click' event listener to a container that has children elements, you may end up clicking one of the children, and e.target will return the child even though the listener in this case is registered on the parent. Stated differently, the target will always return the target element, regardless if the listener is attached to a parent.

event.currentTarget: the element on which the event listener is applied, even if you click on a child. In other words, regardless of which child is clicked the event listener element is set as the currentTarget. Stated differently, what is returned in currentTarget depends on where the listener is registered.

