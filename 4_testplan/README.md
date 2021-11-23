***TEST PLANS***

### 1.TEST ITEMS:
The three major processes that comprise the application are the major test items. In addition, the Game Board, which is a Java Bean, deserves special attention because of the special characteristics of the standard.
##### Test Features : All of  the current features of the application will be tested. In addition, the APIs of the major classes will also be tested.
##### Features not Tested :None
##### Strategy and Approach:
##### Syntax:
DPACT abstract classes are used as the base classes for developing test classes. The methods correspond to test suites, scripts and cases.
##### Description of Functionality : At the system level, the functionality is an electronic version of the Tic Tac Toe  game. Each class provides a specified functionality that is described in its documentation.
##### Arguments for test cases : Mouse clicks
##### Expected Output : It is expected that the appropriate symbol will appear in the selected slot on both Game Boards. When the game completes in either the win/lost or tied states the appropriate message is printed on the Game Board.
##### Specific Exclusions :None
## Test Case Success/Failure Criteria:
At the system test level, test cases result in one of three terminal states for the game: exited, won/lost and tied.
           1.Pass/Fail Criteria for the Complete Test Cycle
Every primary use case must be successful for the application to pass. If any test associated with a primary use case fails, the system test fails.
           2.Entrance Criteria/Exit Criteria
Class testing will be conducted on a continuing basis during development. Integration testing will begin when at least one complete protocol between two classes has been developed. System testing will be initiated when developers/integration testers certify that a game has been completed.
          3.Test Suspension Criteria and Resumption Requirements
Tests will be sequenced to exercise progressively more of the system. Testing will be suspended when program faults prevent the tester from moving further into the system.
Test Deliverables/Status Communications Vehicles
The DPACT-based test classes and the test report are the primary deliverables. The test report will be web-based so that developers can track progress of the testing effort and begin to repair the application before the testing process is complete.

The primary tasks are:
                              1.Test case selection
                              2.Test class construction
                              3.Test execution
                              4.Test result evaluation
                              5.Test report development
Hardware and Software Requirements
The software can be run on either unix or Windows based systems. The tests are derived from the DPACT framework.
Problem Determination and Correction Responsibilities
The tester is responsible for completing a test report that identifies those tests that have resulted in program failure. The developer is responsible for addressing each deficiency identified in the test report.
Staffing and Training Needs/Assignments
Fortunately all of our staff are experienced game players and need no further training to use the application. However, they do need training on calculating the possible combinations of moves.
Tests Schedules
Testing will be completed by 6pm April 19th.
Risks and Contingencies
There are a large number of combinations, (28*1 = 256) of moves that can be made by the two players. Many combinations will not be tested at all. This risk can be mitigated by writing down all the combinations and using a specific one in each test.
       11.Approvals : This plan has been reviewed and approved by the development team leader and the QA department representative.


**TEST CASES**
The switch Player function is slightly more involved than the “reset Board()” function.

The Game State enum contains three possible cases that need to be tested:

The current player is Player A
The current player is Player B
The game hasn’t started yet and no one is the current player.

 Each of these cases will need to be tested to ensure that this function works properly. First, I want to create instances of Player A and Player B to plug into my tests. I could just create them within the function call, but I like to have labels for things:
func testSwitchPlayer() {
	// Player Objects
	let playerA = GameState.playerA
	let playerB = GameState.playerB

The first case I will test is what happens when Player A is the current player:
// Player A Case
let firstPlayerTest = switchPlayer(currentPlayer: playerA)
XCTAssertEqual(firstPlayerTest, playerB)
According to our function logic, if Player A is the current player, then switching the player should return an instance of Player B. Likewise, starting with Player B should return an instance of Player A:
// Player B Case
let secondPlayerTest = switchPlayer(currentPlayer: playerB)
XCTAssertEqual(secondPlayerTest, playerA)
The final test case is what happens where there is no current player. I determined in my logic that Player A would always start, so if we are switching the current player at the beginning of the game, Player A should always be the returned value:
	// Not Currently Playing Case
	let thirdPlayerTest = switchPlayer(
            currentPlayer: GameState.notPlaying)
	XCTAssertEqual(thirdPlayerTest, playerA)
}
