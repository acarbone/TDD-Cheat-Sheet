# Test Driven Development Cheat Sheet

_Inspired by "Test Driven Development by Examples" - Kent Beck_

## What is TDD?

> Drive your development by tests to reach the goal of having clean code that works.

**What should I do?**

1. **Write a test** _As simple as possible_
2. **Make it run** _Quick green excuses all sins but only for a moment_
3. **Make it right** _Refactor_

**Other XP approaches, TDD relates fine to...**

- Pair Programming
- Continuous Integration
- Simple Design
- Refactoring
- Continuous Delivery

## Strategies to quickly go to green

- **Fake it**
Return constants and gradually replace them with working code.
For cases when implementation is not really straightforward.

- **Obvious Implementation**
Directly write working code.
In case implementation is straightforward.

- **Triangulation**
Write more than one test to verify code is working.
Generally to be used when being unsure of the correctness of the abstraction of the calculation.

## How our tests should be?

- **Fast**
Our test suite has to perform as quickly as possible.

- **Isolated**
Success or failure for test A has to be irrelevant for test B coming after.
No state must be maintained within the test suite.

- **Small**
If a test is testing too many things or complex code flows, it requires too much time for the red bar to become green, distracting you and slowing the implementation (and probably the cleanliness of the code).
Difficult testing bits is a design issue and must be solved from a design standpoint.

- **Specific**
Avoid ambiguous assertions that allow multiple results to pass the test.

## Testing Patterns

- **One to Many**
To test collection of objects, first write test for the single object, and then make it work for the collection as well.

- **Fixtures**
Common objects needed by multiple tests: define fixtures as subclasses of TestCase.

- **Step Size**
You can use tiny steps to go forward with the code, or bigger steps depending on the context (todo things, complexity of the implementation, tiredness…).

- **Evident data**
In most cases it is possible to duplicate data within the test to clearly have an idea of how the implementation is expected to work.
Unlikely errors to happen can be tested with “Crash Test Dummy” representing a particular case driving code to errors because of unexpected or weird inputs.

- Commenting out failing tests is **strictly forbidden**. They must be fixed instead.

- **Never remove a test** if, by removing it, your confidence decreases. If two tests has the same behavior, but they express two different cases, leave them both.

## Refactoring

- Dogmatic approach for interruptions is not to have interruptions (for instance some fix to apply that you notice while refactoring something else). In practice you can have brief interruptions, but maximum one at a time (not interrupt an interruption…).

- Use todo list for keeping track of implementations and refactoring activities.

- Remove duplication between test and code as a way to drive design.

- When a new defect gets reported, first thing is to write a test representing that failure and then apply the fix that consequently fixes the new failing test as well.

- **Reconcile differences**: unify two similar pieces of code by adapting one step at a time to bring them closer.

- **Isolate Change**: modify an existing method, isolate the code that has to be changed and then proceed (see Extract Method, Extract Object and Method Object).

- **Migrate Data**: to change data being used, duplicate it to the new version, then switch the implementation to the new one instead of the old format and then change the external API.

- **Extract Method**: a long or complex method has to be split in more pieces of code to be extracted as separate methods.

- **Extract Interface**: introduce a new operation within an already existing shared object, create a new interface with the new op.

- **Method Object**: Complex method with many parameters has to be refactored to a new object with its own methods.

- **Rely on IDEs** refactoring support whenever is possible.

- **Refactoring** without tests drives to errors.

## Stay effective

- What to test? Always write what you want to test in a list before starting. Never take a step forward without knowing where you’re going.

- When new ideas arise, keep note of them, but don’t allow them to distract your attention from what you are implementing.

- Leave the programming session with a broken test so that the next time you get back to the code you know where to start from. When working with a team leave all the tests running, instead.

- Use nested-level-comments to group tests and identify they’re part of a grouped test case

- Test code from external providers ONLY if you can’t trust them.

- Work fresh - If tired or you can’t figure out how to work with a test, take a break.

## Yes, but why? Need some motivation...

- We aren’t striving for perfection. By saying everything two ways - as code and as tests - we hope to reduce our defects enough to move forward with confidence.

- The goal is to write clean code that works.

- Design is not done prior the implementation (analysis approach), but while writing tests, minimizing blockers while analyzing. When I'm trying to add some new functionality, I'm not worried about what really makes a good design for this piece of function, I'm just trying to get a test to pass as easily as I can. When I switch to refactoring mode, I'm not worried about adding some new function, I'm just worried about getting the right design. With both of these I'm just focused on one thing at a time, and as a result I can concentrate better on that one thing.

- Applying design modifications, you don’t have to reason for X minutes to analyze possibilities, but only apply modifications and check whether the tests break. Computer answers in few seconds, when our mind answers in minutes.

- To eliminate duplication.

- It shortens the feedback loop over design decisions.

And check out this influence diagram:

![Anti-TDD influence diagram](/anti-tdd-influence-diagram.jpeg)

_Pressure increases?_

-> **Testing decreases**

_Testing decreases?_

-> **Errors increase**

_Errors increase?_

-> **Pressure increases**

### It becomes a death-spiral.

---

My notes from Kent Beck's "Test Driven Development by Examples"
