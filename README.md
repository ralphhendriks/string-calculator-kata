# String Calculator Kata

The String Calculator Kata is a Test-Driven Development (TDD) kata—an exercise in coding, refactoring and test-first, that you should apply daily for at least 15 minutes.

Roy Osherove published the [original version](https://osherove.com/tdd-kata-1) of the kata. The remainder of this document is a slightly cleaned-up and reformatted version of Roy's original work.

## Instructions

Before you start: 
- Try not to read ahead.
- Do one task at a time. The trick is to learn to work incrementally.
- Make sure you only test for valid inputs. There is no need to test for invalid inputs for this kata.
- Test first!

### Steps

1. Create a simple class `StringCalculator` with a public method with signature

        int Add(string numbers)

    The string parameter `numbers` can contain up to two numbers, separated by commas. The method returns their sum. For an empty string the method returns 0. For example, the string `""` returns 0, the string `"1"` returns 1, and the string `"1,2"` returns 3.

    Hints:
    - Start with the simplest test case of an empty string and then move to cases with one and two numbers.
    - Remember to solve things as simple as possible so that you force yourself to write tests you did not think about.
    - Remember to refactor after each passing test.

2. Allow the `Add` method to handle an unknown amount of numbers.

3. Allow the `Add` method to handle newlines between numbers (instead of commas).

    For example, the string `"1\n2,3"` is valid input and returns 6. The string `"1,\n"` is invalid. Remember, there is no need to test for invalid inputs, the example is just for clarification.

4. Support different delimiters

    To change a delimiter, the beginning of the string will contain a separate line that looks like `"//[delimiter]\n[numbers…]"`. For example, `"//;\n1;2"` returns 3.

    The first line is optional. All existing scenarios must still be supported.

5. Calling `Add` with a negative number will throw an exception 'negatives not allowed' and the negative that was passed.

6. If there are multiple negatives, show all of them in the exception message.

**STOP HERE if you are a beginner. Continue if you can finish the steps so far in less than 30 minutes.**

7. Add a public method to `StringCalculator` with signature

        int GetCalledCount()

    The method returns the numer times `Add` was called.

    Remember to start with a failing (or even noncompiling) test.

8. Add an event to the StringCalculator class

        public event Action<string, int> AddOccured

    that is triggered after every `Add` call.

    Hint: Create the event declaration first, then write a failing test that listens to the event and proves it should have been triggered when calling `Add`.

    Hint 2: Example:

        string giveninput = null;
        sc.AddOccured += delegate(string input, int result)
        {
            giveninput = input;
        };

9. Numbers bigger than 1000 should be ignored, so adding 2 and 1001 returns 2.

10. Delimiters can be of any length with the following format: `"//[delimiter]\n"`. For example `"//[***]\n1***2***3"` returns 6.

11. Allow multiple delimiters like this: `"//[delim1][delim2]\n"`. For example `"//[*][%]\n1*2%3"` returns 6.

12. Make sure you can also handle multiple delimiters with length longer than one char.
