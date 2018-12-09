## Clean Code

**Naming**

1. Use Intention-Revealing Names

2. Avoid DisInformation

3. Make Meaningful Distinctions

4. Use Pronounceable Names

5. Use Searchable Names

6. Avoid Encoding

7. Avoid Mental Mapping

8. Member Prefixes 
	* dont use prefix m_
	* use set and get.
	
9. Class Names 
	* Avoid words like Manager Controller Processor...

10. Method Names 
	* Methods should haver verb or verb phrase..

11. Don't Be Cute
	
12. Pick One Word Per Concept

13. Dont Pun

14. Use Solution Domain Names

15. Use Problem Domain Names

16. Add Meaningful Context(addrFirstName)

17. Don’t Add Gratuitous Context


**Functions**

1. Small

2. Blocks and Indenting

3. Do One Thing
	* FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.
	* Sections within Functions
	* a function is divided into sections such as declarations, initializations, and sieve. **This is an obvious symptom of doing more than one thing.** Functions that do one thing cannot be reasonably divided into sections

4. One Level of Abstraction per Function

5. Reading Code from Top to Bottom: The Stepdown Rule

6. Switch statement.

7. Use Descriptive Names

8. Function Arguments
	* Common Monadic Forms(one argument)
	
	* Flag Arguments 
		Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. It does one thing if the flag is true and another if the flag is false!
	
	* Dyadic Functions
		Even obvious dyadic functions like assertEquals(expected, actual) are problematic.How many times have you put the actual where the expected should be? The two arguments have no natural ordering. The expected, actual ordering is a convention that requires practice to learn.

	* Triads
	
	* Argument Objects
		
	```Java
	Circle makeCircle(double x, double y, double radius);
	Circle makeCircle(Point center, double radius);
	```

		Reducing the number of arguments by creating objects out of them may seem like
cheating, but it’s not. When groups of variables are passed together, the way x and
y are in the example above, they are likely part of a concept that deserves a name of its
own.


9. Have No Side Effects
	**Side effects are lies. Your function promises to do one thing, but it also does other hidden things.**

10. Output Arguments
	**In general output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.**
	
11. Command Query Separation
	**Functions should either do something or answer something, but not both.**

12. Prefer Exceptions to Returning Error Codes

13. Extract Try/Catch Blocks

14. Error Handling Is One Thing
	This implies (as in the example above) that if the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.

15. The Error.java Dependency Magnet
	Returning error codes usually implies that there is some class or enum in which all the error codes are defined.

	```Java
	 public enum Error {
		OK,
		INVALID,
		NO_SUCH,
		LOCKED,
		OUT_OF_RESOURCES,
		WAITING_FOR_EVENT;
	}
	```	

	Classes like this are a dependency magnet



**Comments**

**One of the more common motivations for writing comments is bad code.**

1. Comments Do Not Make Up for Bad Code

2. Explain Yourself in Code

There are certainly times when code makes a poor vehicle for explanation. Unfortunately, many programmers have taken this to mean that code is seldom, if ever, a good means for explanation. This is patently false. Which would you rather see? This:

```Java
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65))
Or this?
if (employee.isEligibleForFullBenefits())
```

It takes only a few seconds of thought to explain most of your intent in code. In many cases it’s simply a matter of creating a function that says the same thing as the comment you want to write.


3. Good Comments
	
	* Legal Comments (copyright..)
	* Informative Comments

	```Java
		// Returns an instance of the Responder being tested.
		protected abstract Responder responderInstance();

	```


	* Explanation of Intent

	* Clarification

	* Warning of Consequences

	```Java
	// Don't run unless you
	// have some time to kill.
	public void _testWithReallyBigFile()
	{
		writeLinesToFile(10000000);
		response.setBody(testFile);
		response.readyToSend(this);
		String responseString = output.toString();
		assertSubString("Content-Length: 1000000000", responseString);
		assertTrue(bytesSent > 1000000000);
	}
	```


	* TODO Comments
		Whatever else a TODO might be, it is not an excuse to leave bad code in
	the system.

	* Amplification (amplify the importance)


3. Bad Comments

	* Mumbling

	* Redundant Comments

	* Misleading Comments
	
	* Mandated Comments

	* Journal Comments

	```Java
	* Changes (from 11-Oct-2001)
	* --------------------------
	* 11-Oct-2001 : Re-organised the class and moved it to new package
	* com.jrefinery.date (DG);
	* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate
	* class (DG);
	* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate
	* class is gone (DG); Changed getPreviousDayOfWeek(),
	* getFollowingDayOfWeek() and getNearestDayOfWeek() to correct
	* bugs (DG);
	* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
	* 29-May-2002 : Moved the month constants into a separate interface
	* (MonthConstants) (DG);
	* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
	* 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
	* 13-Mar-2003 : Implemented Serializable (DG);
	* 29-May-2003 : Fixed bug in addMonths method (DG);
	* 04-Sep-2003 : Implemented Comparable. Updated the isInRange javadocs (DG);
	* 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
	```

	* Noise Comments

	```
	/**
	* Default constructor.
	*/
	protected AnnualDateRule() {
	}
	```
	
	* Scary Noise
	
	```Java
	/** The name. */
	private String name;
	/** The version. */
	private String version;
	
	```

	* Don’t Use a Comment When You Can Use a Function or a Variable
	```
	// Actions //////////////////////////////////
	```
	
	* Closing Brace Comments
	```Java
	} //**while**
	System.out.println("wordCount = " + wordCount);
	System.out.println("lineCount = " + lineCount);
	System.out.println("charCount = " + charCount);
	} // **try**
	catch (IOException e) {
	System.err.println("Error:" + e.getMessage());
	} //**catch**
	```
	
	* Attributions and Bylines
	```Java
	/* Added by Rick */ use git history
	```
	
	* Commented-Out Code
	
	* HTML Comments

	```Java
	/**
	* Task to run fit tests.
	* This task runs fitnesse tests and publishes the results.
	* <p/>
	* <pre>
	* Usage:
	* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
	* classname=&quot;fitnesse.ant.ExecuteFitnesseTestsTask&quot;
	* classpathref=&quot;classpath&quot; /&gt;
	* OR
	* &lt;taskdef classpathref=&quot;classpath&quot;
	* resource=&quot;tasks.properties&quot; /&gt;
	* <p/>
	* &lt;execute-fitnesse-tests
	* suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
	* fitnesseport=&quot;8082&quot;
	* resultsdir=&quot;${results.dir}&quot;
	* resultshtmlpage=&quot;fit-results.html&quot;
	* classpathref=&quot;classpath&quot; /&gt;
	* </pre>
	*/
	```


	* Nonlocal Information

	```Java
	/**
	* Port on which fitnesse would run. Defaults to <b>8082</b>.
	*
	* @param fitnessePort
	*/
	public void setFitnessePort(int fitnessePort)
	{
		this.fitnessePort = fitnessePort;
	}
	```

	* Too Much Information
	
	Don’t put interesting historical discussions or irrelevant descriptions of details into your
	comments.

	* Inobvious Connection

	The purpose of a comment is to explain code that does not explain itself. It is a pity
	when a comment needs its own explanation.

	* Function Headers

	Short functions don’t need much description. A well-chosen name for a small function that
	does one thing is usually better than a comment header.

	
	**Formating**

	1.Vertical Formatting

	Small files are usually easier to understand than large files are.

	* The Newspaper Metaphor

	The topmost parts of the source file should provide the high-level concepts and algorithms. Detail should increase as we move downward, until at the end we find the lowest level functions and details in the source file.

	* Vertical Openness Between Concepts

	* Vertical Density

	Concepts that are closely related should be kept vertically close to each other

	Variable Declarations. Variables should be declared as close to their usage as possible. Control variables for loops should usually be declared within the loop statement

	* Vertical Distance

	Concepts that are closely related should be kept vertically close to each other 

	**Variable Declarations**. Variables should be declared as close to their usage as possible.

	**Instance variables**, on the other hand, should be declared at the top of the class. 
	This should not increase the vertical distance of these variables, because in a well-designed class, they are used by many, if not all, of the methods of the class.

	The important thing is for the instance variables to be declared in one well-known place. Everybody should know where to go to see the declarations.

	**Dependent Functions**. If one function calls another, they should be vertically close,
	and the caller should be above the callee, if at all possible.

	**Conceptual Affinity**. Certain bits of code want to be near other bits. They have a certain
	conceptual affinity. The stronger that affinity, the less vertical distance there should be between them.	



