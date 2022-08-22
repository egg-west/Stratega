# Run a fast experiment for Kill The King game with Elastic-MCTS against MCTS
1) Install Visual Studio 2019
2) Clone this repository
3) Open `Strategy` folder with VS2019
4) Compile x64-Release and run `Arena.exe`

**To see argument used in the experiment, please see the screen output or locate `Stratega/resources/gameConfigurations/TBS/KillTheKing.yaml`**
The `.yaml` file looks like: 

```yaml
    - UnitMCTSAgent:
        Budget: FMCALLS
        DoStateAbstraction: true
        MaxFmCalls: 5000
        RolloutLength: 10
        ContinuePreviousSearch: false
        AbstractionBatch: 8
        K: 0.1
    - UnitMCTSAgent:
        DoStateAbstraction: false
        Budget: FMCALLS
        MaxFmCalls: 5000
        RolloutLength: 10
        ContinuePreviousSearch: false
```

The screen output looks like

```
The maps file exist
Initializing new game
Player 0 is controlled by ElasticMCTSuAgent
Player 1 is controlled by MCTSuAgent
Agent with parameters:
        PLAYER_ID: 0
        Budget type: Forward Model calls
        Max FM Calls (active): 5000
        Max Iterations (inactive): 10
        Stop at Perc Time (inactive): 0.9
        Current FM Calls: 0
        Current iterations: 0
        Scripts in portfolio: 0
        Opponent model by script: RandomActionScript
        State evaluation heuristic: AimToKingHeuristic
ElasticMCTSuParameters
        K = 0.1
        ROLLOUT_LENGTH= 10
        ROLLOUTS_ENABLED= 1
        PRIORITIZE_ROOT= 1
        MAX_FM_CALLS= 5000
        EPSILON = 0.01
        CONTINUE_PREVIOUSE_SEARCH = 0
        DO_STATE_ABSTRACTION = 1
        R_THRESHOLD = 0.1
        T_THRESHOLD = 0.3
        earlyStop = 8
```



You can check `Stratega/out/build/x64-Release/bin/sgaLog.yaml` for logs. It looks like this

```yaml
Game 1:
  Map: 1
  Seed: 4692272
  Battle0:
    PlayerAssignment: [ElasticMCTSuAgent, MCTSuAgent]
    ActivePlayer: [0, ..., 0]
    ActionCount: [25, ..., 5]
    WinnerID: 0
    Turns: 28
  Battle1:
    PlayerAssignment: [MCTSuAgent, ElasticMCTSuAgent]
    ActivePlayer: [0, ..., 1]
    ActionCount: [25, ..., 26]
    WinnerID: 1
    Turns: 24
```



**To cite this paper**

```
@article{xu2022elastic,
  title={Elastic Monte Carlo Tree Search with State Abstraction for Strategy Game Playing},
  author={Xu, Linjie and Hurtado-Grueso, Jorge and Jeurissen, Dominic and Liebana, Diego Perez and Dockhorn, Alexander},
  journal={arXiv preprint arXiv:2205.15126},
  year={2022}
}
```