

link to codecademy lesson

https://github.com/gladstone28/Automate-and-Organize-Tests-Install-Mocha_I

other link

https://www.codecademy.com/journeys/full-stack-engineer/paths/fscj-22-front-end-development/tracks/fscj-22-javascript-testing/modules/wdcp-22-write-good-tests-with-mocha-764e85ca-0abf-4da9-91a2-43f8d593eab8/lessons/automate-organize-tests/exercises/hooks


### Automate and Organize Tests

**Hooks**

Over the last two exercises, we learned about the four main phases of a test: setup, exercise, verify, and teardown. In the last exercise, you may have noticed that the setup and teardown steps were identical between tests.

While execution and verification are unique to each test, setup and teardown are often similar or even identical for multiple tests within a test suite. The Mocha test framework provides Preview: Docs Loading link description functions that enable us to reduce repetition, simplify the scope of each test, and more finely control the execution of our tests.

These functions (also referred to as hooks) are:

beforeEach(callback) - callback is run before each test
afterEach(callback) - callback is run after each test
before(callback) - callback is run before the first test
after(callback) - callback is run after the last test Each hook accepts a callback to be executed at various times during a test. The before... hooks naturally happen before tests and are useful for separating out the setup steps of your tests. Meanwhile, the after... hooks are executed after tests and are useful for separating out the teardown steps of your tests.
describe('messing around with hooks', () => {

  let testValue; // Variable used by both tests

  beforeEach(() => {
    testValue = 5;
  });

  it('should add', () => {
    // testValue = 5 <-- moved to beforeEach()
    testValue = testValue + 5;
    assert.equal(testValue, 10);
  });

  it('should multiply', () => {
    // testValue = 5 <-- moved to beforeEach()
    testValue = testValue * 5;
    assert.equal(testValue, 25);
  });

});
In this example, while each it() block could have set the testValue to 5, using the beforeEach() hook allows us to avoid that repetition while keeping each test isolated.

Keep in mind that not all setup and teardown steps should be included in these hooks. Occasionally, you may find that you need to perform some unique setup or teardown for a single test that you don’t want to include in other tests.
