# Day 5 Mazes III

```template
let endBlock = 0
player.onChat("maze", function () {
    if (agent.inspect(AgentInspection.Block, DOWN) == 42) {
        agent.teleport(agent.getPosition(), EAST)
        endBlock = 41
    } else if (agent.inspect(AgentInspection.Block, DOWN) == 41) {
        agent.teleport(agent.getPosition(), WEST)
        endBlock = 42
    } else {
        agent.teleport(world(17, 0, 8), EAST)
        endBlock = 41
    }
})
```

## Mazes III

This is the third time we've seen mazes this week. Are you ready for your final maze challenge? Learn from Sensei about the Right-Hand Maze Algorithm!

## Algorithms?

An algorithm is a set of rules or instructions that are followed to complete a task. It's like a sequence, but instead of having a set of random instructions, all the instructions work together to accomplish a specific goal. Unlike the first or second time we had activities with Mazes, this time we will be making an Algorithm that can solve (almost\*) any maze! <br><br>
\*Mazes have to be "simply connected" for this algorithm to work. As far as we are concerned for this activity, this just means that the end point has to be along the outside wall of the maze, not somewhere in the middle.

## Step 1 

You've been provided a starter for the chat command "maze". This code will make sure that the agent is in the right place and facing the right direction to head toward the exit of the maze. If the agent starts on iron then it heads to gold, if it starts on gold then it heads to iron, and if it starts somewhere else, it decides to start from iron.


## Step 2

Listen to Sensei to learn how to make a ``||functions.function||`` that helps the agent get to the goal!

## Code Complete

Did you follow along with Sensei? You can use the hint to check your code!

```blocks
    let endBlock = 0
function rightHandMaze () {
    while (agent.inspect(AgentInspection.Block, DOWN) != endBlock) {
        if (agent.detect(AgentDetection.Block, RIGHT)) {
            while (agent.detect(AgentDetection.Block, FORWARD)) {
                agent.turn(LEFT_TURN)
            }
            agent.move(FORWARD, 1)
        } else {
            agent.turn(RIGHT_TURN)
            agent.move(FORWARD, 1)
        }
    }
}
player.onChat("maze", function () {
    if (agent.inspect(AgentInspection.Block, DOWN) == 42) {
        agent.teleport(agent.getPosition(), EAST)
        endBlock = 41
    } else if (agent.inspect(AgentInspection.Block, DOWN) == 41) {
        agent.teleport(agent.getPosition(), WEST)
        endBlock = 42
    } else {
        agent.teleport(world(17, 0, 8), EAST)
        endBlock = 41
    }
    rightHandMaze()
})

```

## Activity Complete!

Great job! You learned about functions and algorithms! As a bonus question, do you think you could make a left-hand maze algorithm? Would it work? Would the agent take the same path? Why or why not?
