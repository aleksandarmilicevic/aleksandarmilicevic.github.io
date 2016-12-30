Available UROP Projects
===

  **group**:   | [Software Design Group](http://sdg.csail.mit.edu/) <br/>
  **PI**:      | [Prof. Daniel Jackson](http://people.csail.mit.edu/dnj/) (<dnj@csail.mit.edu>)<br/>
  **contact**: | [Aleksandar Milicevic](http://people.csail.mit.edu/aleks/) (<aleks@csail.mit.edu>)<br/>

* **[Domain-specific language for Alloy embedded in Ruby][p1]** 
* **[Application agnostic Javascript front-end for a model-based Rails framework][p2]** 
* **[Event-driven paradigm for ROS (Robot Operating System)][p3]** 
* **[Customization UI for visualization algorithms in Alloy][p4]** 

---

### Domain-specific language for Alloy embedded in Ruby

  **topics**: programming language design, symbolic execution, formal
              language semantics, first-order logic, constraint
              solving, parsing.

  **goal**: Design, implement, and formalize an embedded
            domain-specific language for writing and analyzing Alloy
            models directly in Ruby.

  **technologies**: Ruby, Alloy.

[Alloy][1] is a first-order, relational, modeling language.  Alloy is
declarative (based on logic), and as such, it is not executable per
se; it is instead used primarily to formally model systems for the
purpose of checking various logical properties against them.  Most of
Alloy’s expressive power, however, comes from its relational base and
its relational operators, which, in contrast, can be efficiently
executable in the context of object-oriented programs.  Even the
first-order quantifiers ("all" and "exists") can be executed using a
straightforward iterative search over the bounded domains of
quantified variables, which can be appropriate when the domain is
small and/or the constraints are simple.

The main goal of this project is to design a language for writing
Alloy models directly in Ruby, which are at the same time fully
executable, just as any other Ruby programs.  The idea is to find a
middle ground and have a single language with two execution modes:
symbolic (translates to Alloy) and concrete (executes directly in the
Ruby interpreter).  This would allow it to be used either (1) mostly
as a modeling language (for writing complex models in logic for the
purpose of formal analysis, but having a full-blown Ruby for any
pre/post-processing), (2) mostly as an imperative OO programming
language inside Ruby, with added benefits of runtime checks of simple
properties, or (3) anywhere in between.

We have already implemented most of the syntax of this new language,
and also some of the translation (by means of symbolic execution) into
logical Alloy expressions, so we have a good understanding as to in
which directions to proceed.  The student joining this project would
work on completing this translation, designing the missing parts of
the language (possibly redesigning some existing ones) and
interoperating with the existing Java-based solver for the Alloy
language (meaning that it should offload the collected logical
expressions to the Alloy solver and bring the solution back to Ruby).
This project spans across many topics of programming language research
(listed above; familiarity is by no means a prerequisite), and being
involved in such a broad project would be of great benefit to someone
interested in pursuing graduate education in the area of programming
languages and program analysis.

---

### Application agnostic Javascript front-end for a model-based Rails framework

   **topics**: model-based GUI, GUI design, widget library design,
               interactive/responsive web interface.

   **goal**: Design and implement an application-agnostic,
             Javascript-based front end for an existing model-based
             web application framework for Rails.

   **technologies**: Javascript, Ajax, jQuery, [your favorite JS
                     widget library], Ruby on Rails.

We have implemented a model-based web framework on top of Ruby on
Rails for building event-driven interactive web applications.  The
core of our framework is an information-rich model which enables the
framework to automatically synthesize many parts of the application at
runtime, on the fly.  For example, there are no controllers, and the
programmer does not have to write database migrations, ActiveRecrod
association ends (reflections), routes, etc.  Furthermore, the
framework keeps track of all connected clients and the data they are
displaying, so whenever the value of a piece of data changes, the
framework immediately propagates that change to all relevant clients
(using the "server push" mechanism).  The clients then know how to
automatically refresh their views (by updating the DOM), thanks to our
smart views (written as regular templates but data binding enabled);
as a result, the programmer does not have to write any Ajax code to
get a responsive, auto-refreshing GUI.

Currently, the programmer has to manually write the views for his or
her application (which are conceptually no different from the standard
ERB templates commonly used in Rails applications).  This part,
however, could also be automated, which is exactly the main goal of
this UROP project.  Our framework could provide a generic user
interface, directly generated from the core application model, which
simply allows the user to view and query the current object state.

The student joining this project should already be comfortable with
Javascript, and ideally familiar with some Javascript UI libraries, as
this project is mostly about designing snappy looking widgets for
visualizing the application object state.  The most challenging part
of the project is to come up with a clever, generic, model-based UI,
preferably customizable so that it can be tweaked and fine tuned
differently for different concrete applications.

This is not a building a one-off GUI for a given app kind of project;
rather, this project is about building a set of generic,
template-based widgets, that reflectively read the application model
(e.g., "what are the all different model classes in this system?",
"what are the fields of this particular model class and what are their
types?", etc.), and dynamically query the application state (e.g.,
"give me all the instances of this class", "what is the value of this
field in this concrete instance", etc.), and displays all that data in
a meaningful and intuitive way.  Fortunately, all these technical and
infrastructural problems are already taken care of, so the student
will be able to focus solely on being creative and designing a nice
general-purpose GUI.


---

### Event-driven paradigm for ROS (Robot Operating System)

   **topics**: robot programming, event-driven programming, framework
               design.

   **goal**: Port an existing framework for event-driven programming
             to ROS (Robot Operating System).

   **technologies**: ROS, Python or Java.

Robot programming for novice users is becoming increasingly
attractive.  Most robot programs are inherently distributed and
event-driven, while distributed programming is, however, often
difficult and error-prone even for experienced programmers. 

We have designed an approach for event-driven programming of
general-purpose distributed systems which allows the programmer to
have a simple sequential semantics and a unified model of the system
as a whole.  Consequently, the programmer does not have to worry about
data consistency and concurrency bugs, as our runtime framework is in
charge of synchronizing all requests and keeping all nodes updated.
We have implemented a prototype of this approach for client-server
applications in Java.

As Java is not commonly used for robot programming, the main goal of
this UROP project is to port our existing Java implementation to ROS,
and further adapt it to the particular needs of robot programmers.
ROS already provides many high-level concepts for message passing
communication between the nodes, so implementing our event-driven
concepts for ROS should be much simpler than doing the same for Java.
The most interesting part of this project should be learning about
ROS, identifying common programming tasks in robotics, and
re-implementing those tasks as examples using the new event-driven
framework.

This project is most suitable for a student interested in robotics,
and learning more about robot programming in ROS.  ROS officially
supports Python as one of the front-end programming languages, but
also has "experimental" front-end for a subset of Java (compatible
with Java for Android), so the student will get to choose between
those two target platforms.

---

### Customization UI for visualization algorithms in Alloy
   
   **topics**: UI design, framework design.

   **goal**: Implement a Swing UI for configuration and customization
             of visualization algorithms in Alloy Analyzer.

   **technologies**: Java, Swing, UI, Alloy.

The [Alloy Analyzer][1] is an automated constraint solver for
first-order relational logic.  Alloy represents found solutions as
typed object graphs, which are automatically visualized (using a
predetermined layout algorithm) and presented to the user.

We have recently implemented a set of new layout algorithms, which
provide more flexibility, but also require certain configuration by
the user.  One of the most exciting new features is the notion a
composite layout algorithm, where the user can select different layout
algorithms to be used for different parts of the object graph.  The
only missing part, which is the main task of this project, is to
implement a UI to allows the user to make that selection in a visual,
convenient and intuitive way.

Aside from using Java and Swing to develop UI widgets, the student
will also learn about, and will have to work (to some extent) with,
Alloy's first-order relational logic and automated solver, which is a
very valuable and exciting topic for someone interested in continuing
to study programming languages, constraint solving, software analysis,
and software design.

   [1]: http://alloy.mit.edu "Alloy---first-order relational model finder"
   [p1]: #domain-specific-language-for-alloy-embedded-in-ruby
   [p2]: #application-agnostic-javascript-front-end-for-a-model-based-rails-framework
   [p3]: #event-driven-paradigm-for-ros-robot-operating-system
   [p4]: #customization-ui-for-visualization-algorithms-in-alloy