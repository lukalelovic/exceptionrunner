Tasks to answer in your own README.md that you submit on Canvas:

1. See logger.log, why is it different from the log to console?
   The exception thrown in the fail case does not log to the logger.log file, but does display the exception within the console.
2. Where does this line come from? FINER org.junit.jupiter.engine.execution.ConditionEvaluator logResult Evaluation of condition [org.junit.jupiter.engine.extension.DisabledCondition] resulted in: ConditionEvaluationResult [enabled = true, reason = '@Disabled is not present']
   Comes from Junit when running the Tester. Junit is checking whether a disabled test method is present, and if there are not any it is being logged as finer.
3. What does Assertions.assertThrows do?
   Passes the test case if the correct exception was thrown, and fails if it was not thrown based on the given input.
4. See TimerException and there are 3 questions
    1. What is serialVersionUID and why do we need it? (please read on Internet)
       All exception classes are serializable, and all serializable classes must have a serialVersionUID in order to version the serialized data. This is then used when deserializing to check how the serialized data matches the code. 
    2. Why do we need to override constructors?
       Because the subclass has a different class name than the superclass, and therefore the superclass constructor will not be called by default. Must use “super ()” to call superclass constructor or overriden method.
    3. Why we did not override other Exception methods?
       We always want our TimerException to have a message, and never want to suppress the exception or write the stack trace.
5. The Timer.java has a static block static {}, what does it do? (determine when called by debugger)
   Used for static initialization of the Tester class the first time the class is initialized. Gets the logger properties and configurations.
6. What is README.md file format how is it related to bitbucket? (https://confluence.atlassian.com/bitbucketserver/markdown-syntax-guide-776639995.html)
   Markdown style format. This is the format for all README files on bitbucket.
7. Why is the test failing? what do we need to change in Timer? (fix that all tests pass and describe the issue)
   A TimerException was expected, but a NullPointerException was thrown instead. This occurred because in the finally block of the try/catch it is assumed timeNow is not null. Need to change this to account for timeNow being potentially null.
8. What is the actual issue here, what is the sequence of Exceptions and handlers (debug)
   Timer edge case is called first and has no exceptions thrown, but handles a potential TimerException. Fail case is executed next, and throws an unhandled NullPointerException while expecting a TimerException to be thrown. Lastly the pass case executes and does not throw any exceptions, but handles a potential TimerException if one were to be thrown.
9. Make a printScreen of your eclipse JUnit5 plugin run (JUnit window at the bottom panel) 
10. Make a printScreen of your eclipse Maven test run, with console.
11. What category of Exceptions is TimerException and what is NullPointerException?
    TimerException is a checked exception, while NullPointerException is a type of unchecked exception.
12. Push the updated/fixed source code to your own repository.