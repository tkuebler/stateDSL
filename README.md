
# stateDSL

An event driven FSM DSL for Unity and C#.

## Objective

Create a trivial to use FSM DSL that can be embedded in a C# Unity environment.

Design Goals ( Wish List ):

1. Supports Unity's 'script per behavior / gameobject' pattern.  ie. easy to use with standard programming practice in unity.
1. Co-habits regular C# game behavior scripts.
1. Is terse and easy to read without documentation.  It should be completely obvious from example.
1. Explict without boilerplate.
1. Support MonoBehavior objects and be main thread safe/aware.
1. Supports user provided events
1. Provides hooks into unity's event framework
1. Unity package with examples.

Optional (Unicorns Eating Pie in Sky):

1. SubState Machines at any node.
1. Unity Editor Graphical Viewer 
	1. Shows your FSMs across all your unity scripts in easyt to read graph format.
	1. Shows your current transtions and states during play mode.
1. Support for javascript.
1. Support for delegate subscription to events ( faster than unity's events )

##Example:

```cs
	// script #1
	FSM Example {
	
		state default {
			on_entry { // C# code here }
			exit { // C# code here }
		
			// catchall events
			on_event {
				// C# code here
				....
				state two; // transition to state 2
			}
		}
	
		state two {
			entry { // your C# }
			exit { // your C# }
		
			// catch event A
			event A {
				// C# code here
				state three;
			}
			// catch all other events
			event {
				// C# code here
			}
	}
```	
------
```cs
	// Script #2
	FSM Example {
		state three {
			entry { // your C# }
			exit { // your C# }
			event A {
				// C# code
				state two
			}
			event B {
				// C# code
				state default;
			}
			event C { // C# code }
		}
```

## Footnotes:

- https://en.wikipedia.org/wiki/Linden_Scripting_Language
- http://wiki.secondlife.com/wiki/State
- https://github.com/jenkinsci/job-dsl-plugin/wiki/Tutorial---Using-the-Jenkins-Job-DSL
- https://helpercode.com/2012/07/16/fluent-interfaces-in-c-extension-methods/
- https://martinfowler.com/dslCatalog/
- https://martinfowler.com/dsl.html
