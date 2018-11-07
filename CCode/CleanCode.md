### Clean Code

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
	![alt text](dont_be_cute.PNG "don't be cute")

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
		```
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

	```
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

```
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65))
Or this?
if (employee.isEligibleForFullBenefits())
```

It takes only a few seconds of thought to explain most of your intent in code. In many cases it’s simply a matter of creating a function that says the same thing as the comment you want to write.


3. Good Comments
	
	* Legal Comments (copyright..)
	* Informative Comments

	```
		// Returns an instance of the Responder being tested.
		protected abstract Responder responderInstance();

	```


	* Explanation of Intent

	* Clarification

	* Warning of Consequences

	```
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

	```
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



	