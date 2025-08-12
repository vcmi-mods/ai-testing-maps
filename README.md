# Maps for AI testing

For all test maps there are rules I tried to stick to:

* Our testing player is always Red. Red *pretend* to be human player since in H3 some mechanics only work for player.
* In same time limitations like patrol has to apply on player.
* On map with two players our enemy is Blue.
* On maps needed teams our ally is always Blue and enemy is Tan.
* Tests that depend on exact resources amounts all must have
* Timed Event set to remove all resources on start.
* Resources are default for normal difficulty.
* All map should be visible for AI as long as map description
 not specify otherwise. On most maps AI wouldn’t be able to fail by wasting time on wandering, but there always chance few would fail because of it.
* There should be no starting bonus or it’s must be resources.
* Starting artefact as bonus could affect result in some tests.
* Maps with “F” in name before test sub id are MUST_LOSE test.
* Maps with “A” suffix after sub id are alternative versions of same test. E.g original test might be checking result through victory condition and other through Quest Guard. This sometimes useful since AI isn’t always doing something we want while in other case it does.
* All maps that require exact resources amounts take 99999 of all resources by Timed Event on start.

## Docomentation

Available at https://docs.google.com/document/d/1Dro_0GncWYp2KZCPQiEDiapOHViJobyYB3hkpF5CeKE/edit?tab=t.0

## Meaning of tags within map description

For now maps are self-contained and map description could contan following “tags”. They inconsistent at times and can certainly be improved.

| Tag Name | Meaning |
| ------------- |:-------------:|
| MUST_WIN | AI expected to win this map. |
| MUST_LOSE | AI expected to lose this map. |
| MUST_TIMEOUT | Map should stuck since victory condition is wrong. These tests should be reworked. |
| DEADLINE_WEEK | Map has a loss condition set after a week since AI must get to the goal earlier. |
| DEADLINE_4WEEKS | This and other alike it  |
| DEADLINE_CUSTOM | Since loss condition already used for something else there is enemy hero going to arrive by ship delayed by embark / disembark. See test 0460. Another option is to use Timed Event that give resources and Quest Guard. |
| REPEAT_TIMES_20 | Test must be repeated N times to get proper results. By default it's mean player must lose or win every time. |
| REPEAT_CAN_LOSE | For this test at least one corrent return is sufficient. So if condition is win it's fine for AI to lose few times and testing stopped on first time correct result achieved. |
| REPEAT_CAN_WIN | Other way around. |
| REPEAT_NEVER_LOSE | AI should never lose during repeats to pass test. |
| REPEAT_NEVER_WIN | Other way around. |
| H3FAIL | H3 AI failed to pass the test since gameplay behaviour is incorrect or it’s not implement feature. |
| H3CRASH | H3 crashed on this test. |
| H3BUG | H3 is bugged on this test. |
| DUMMY_TEST | Test only make sure game not crashing / freezing, but not actually prove that gameplay mechanics working properly.  |
| BATTLE_IMPORTANT | Test where it’s important for Battle AI to work properly in order to pass the test. |
| LONG_TEST | Test may take a lot of time to complete. |
| TEAM_TEST | Test affected by alliance mechanics. |
| AIBEHAVIOR_IMPORTANT | Test might not work properly depend on AI behaviour. |
| CHEAT_TEST | Test that include some kind of cheating / exploiting mechanics. |
| FOW_TEST | Test that depend on realistic FoW so AI shouldn’t know the map in the beginning. |
