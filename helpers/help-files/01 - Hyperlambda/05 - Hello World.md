## Hello World

In this chapter we are going to create our first Hyperlambda application called *"Hello World"*. By walking through this application, 
and explaining what it does, you will be armed with the knowledge required to create your own Ajax web apps.
First make sure you select the _"/modules/"_ folder in the file explorer to your left. Then click the _"+"_ button, which will open
up a wizard form for you, allowing you to create a new application. Name your app `hello-world`, make sure you select the _"hello-world"_
template project (*type* that is), and click _"Create"_.

This will create a new project for you, and automatically open up its _"launch.hl"_ file. If you open up another tab window, by
clicking [here](/hello-world), you can test your application immediately, assuming you named your app **exactly** _"hello-world"_.
If you try to click the button in your app, it will change its value.

### Your app's file structure

There are 5 files that most Phosphorus Five apps, or modules more accurately will have. These are as follows.

* _"launch.hl"_, which is the file that is evaluated when your app is launched
* _"startup.hl"_, which is evaluated every time the server restarts for some reasons
* _"install.hl"_, which is evaluated when the app is installed (does not exist in our _"Hello World"_ example application)
* _"uninstall.hl"_, which is evaluated when the app is uninstalled
* _"desktop.hl"_, which becomes you app's _"desktop icon"_

All of the above files are optional when creating a new module, and some modules will have some of the above files, but not all of them. Our
little _"Hello World"_ app will only have 4 of these files. Feel free to open these files, and study them, to get more understanding of what 
they actually do. They should be heavily commented, for your convenience.

### Hyperlambda's structure

Hyperlambda is a name/value/children file format. It allows you to declare *"graph objects"*, or *"tree structures"* - And is semantically 
quite similar to JSON. In Hyperlambda, we refer to such tree structures declared by Hyperlambda as *"lambda objects"*.
Think of it like the relationship between JSON (Hyperlambda), and the JavaScript objects after your JSON has been evaluated (lambda). 
If you still think this is difficult to understand, you can watch the following video, describing the relationship between Hyperlambda and 
lambda.

**Warning**, the videos here are pretty old, and they're using System42, which is **obsolete** today. Feel free to rather just use the
Hyper IDE editor, editing your _"launch.hl"_ file for example, if you wish to reproduce what I do in these next two videos. The videos
are also created (arguably) such that a child should be able to uderstand them. If you feel that I am being too thorough, please have 
that in mind as you watch them.

https://www.youtube.com/watch?v=oML2JE8kAO0

### Analyzing our code

In our _"launch.hl"_ file, we have a **[create-widget]** invocation. This declare a *"lambda node"*. The node has several children
nodes, such as a **[class]** node, and a **[widgets]** node. To declare a child of another node in Hyperlambda is very easy, all you have to do, 
is to indent your node with two spaces, relative to the indentation of the node you wish to declare these children inside of. This 
makes sure that your node becomes a child of the node above it, or an *"argument"* if you wish.

In addition, we invoke the **[p5.web.include-css-file]** event, passing in the paths to 3 CSS files. These are a part of Micro, which
is the subject of another part of the help system - But basically Micro is an alternative to Bootstrap CSS, for those who are acquinted with
Bootstrap.

### Ajax events

In our example above, we have a couple of **[onclick]** Ajax event for our buttons. This will create an *"onclick"* DOM event handler for 
us, which when raised, will create an Ajax request, going towards our server, invoking its lambda object.
Lambda objects, such as the one we have declared inside our **[onclick]** event handler, is often referred to as simply *"lambda"*. Lambda 
objects are stored function objects, which are executed, whenever some condition is being met - Or we wish to for some reasons execute our 
lambda. The simplicity in declaring such *"lambda objects"*, is the reason why Hyperlambda got its name.

The *"lambda"* object for our _"Hello World"_ button, simply invokes the **[set-widget-property]** Active Event, with the ID of *"foo-button"*, 
and an **[innerValue]** argument of *"Hello World"*. This changes the **[innerValue]** property of our *"foo"* widget, to whatever HTML we 
pass in as the value of our **[innerValue]** argument. The **[set-widget-property]** is an alias to **[p5.web.widgets.property.set]**, 
which you will see other places in our P5 examples. Many Active Events have aliases, which are alternative names, for invoking the same 
Active Event.

### The CSS structure

Micro, which is the CSS framework we are using here, has a similar structure to Bootstrap CSS. Basically a _"container/row/col"_ structure, 
where each _"col"_ must be put into a _"row"_, and each _"row"_ must be put into a _"container"_. This is why we need to create some
wrapper widgets, wrapping our button, before we can declare our actual button. We could of course have create our button directly, without
neither any Micro CSS parts, nor and of the wireframing widgets around it - But this would create an _"ugly"_ result for us. Yet again, Micro
is the subject of another part of this documentation.

### Additional studying, video tutorial

If you still struggle with some of the parts we walked through in this chapter, you might benefit from watching the following video.

https://www.youtube.com/watch?v=O9ek7JH7Ptw