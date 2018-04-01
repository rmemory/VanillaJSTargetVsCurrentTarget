This project demonstrates the difference between a JS event.target and event.currentTarget. It and the explanation is provided courtesy of https://github.com/mmemory

event.target: the element on which the event occurred. If you add an 'click' event listener to a container that has children elements, you may end up clicking one of the children, and e.target will return the child even though the listener in this case is registered on the parent. Stated differently, the target will always return the target element, regardless if the listener is attached to a parent.

event.currentTarget: the element on which the event listener is applied, even if you click on a child. In other words, regardless of which child is clicked the event listener element is set as the currentTarget. Stated differently, what is returned in currentTarget depends on where the listener is registered.

(1) When you click outside of any of the "controls" (ie. buttons), and you will see the document listener has fired. For "target", it gives an HTMLNode which points at the html tag. For "currentTarget", it provides the document DOM element.

Stated differently, it seems in this case both document.target and document.currentTarget point at the same thing, the only difference is one is a HTMLNode and the other is a DOM Node, and since we are talking about the document listener, that seems to make sense.

(2) Next, click on blue background box associated with the "Click me too" button (ie. the div with an id of "parent"). For this, you will see both the parent and document listeners have fired. 

For a description of the difference between "document" and "parent" see this:

https://www.w3schools.com/jsref/prop_node_parentnode.asp

"The parentNode property returns the parent node of the specified node, as a Node object.".

This explains why the parent listener didn't fire in case (1) above.

The document.currentTarget does point at the document element, which makes sense (ie. the document listener is tied to the document element). 

(3) Next, click on the "Click me too" button, and you'll see three listeners have fired: child, parent, and document. 

The child.target and child.currentTarget point at the button. The parent.target also points at the button, while parent.currentTarget points at the div. The document.target also points at the button, and document.currentTarget points at the document. All of this makes sense. 

See the index.html for the example in Vanilla JS Sound,

https://github.com/rmemory/VanillaJSSound

As a test, I add the following to my listener (inside of the currentTarget conditional):

console.log(e.target);
console.log(e.currentTarget);

When you click on the "A" kbd tag. you'll see that e.target returns the kbd HTML node, and e.currentTarget returns the parent of of the kbd, in this case a div. And this matches my understanding of what I am seeing in this project's index.html. The listener in my code is tied to the div (aka, currentTarget), which is a parent of the kbd (aka, target).

Also see this:

https://stackoverflow.com/questions/5921413/difference-between-e-target-and-e-currenttarget

In the comments, I noticed this:

"e.target = The thing under the mouse (as ben says... the thing that triggers the event). 
e.currentTarget = The thing before the dot... (see below)"

On the surface, I am not sure I fully follow "The thing before the dot" part of that comment, but this comment helps:

"e.target will be one of the 10 buttons and e.currentTarget will always be the "btns" clip."

In his example, "btns" is the container (div or otherwise), which in turn contains ten buttons. 
