# GAME_PROGRAM-EX--7

# AIM
To create an AI character in Unreal Engine that roams randomly within a NavMesh area and chases
the player when they come within a certain range, using Behavior Trees, Blackboard, and AI
Perception.

## STEPS
1. Setup Navigation
Add a NavMeshBoundsVolume to your level and scale it to cover the roamable area.
Press P to confirm the green nav area is visible (indicating navigable space).
2. Create AI Character
Create a Blueprint character (e.g., BP_AIEnemy ) with a skeletal mesh and AIController class.
Create an AI Controller Blueprint (e.g., BP_AIController ) and assign it to the character.
3. Enable AI Perception
In BP_AIController , add an AIPerception component.
Configure a Sight sense (set detection range, lose sight range, peripheral vision angle).
Bind OnPerceptionUpdated to update a blackboard value
(e.g., CanSeePlayer and PlayerActor ).
4. Set Up Blackboard
Create a Blackboard with the following keys:
TargetLocation (Vector)
PlayerActor (Object)
CanSeePlayer (Bool)
5. Create Behavior Tree (BT_AI)
Structure it like this:
AI Random Roam with Chase - Unreal Engine 🎯 Aim

## Procedure
Root
Selector

Sequence (Chase Player)

Blackboard Check: CanSeePlayer == truTask: Find Random Location → TargetLocation
Move To: TargetLocation

6. Custom Task: Find Random Location
Create a new BTTask_BlueprintBase to get a random reachable point using:
Set the result to the TargetLocation blackboard key.

8. Test the AI
Add a player character to the level.
Place the AI enemy in the map and assign its controller and behavior tree.
Press Play: the AI should roam when the player is far and chase the player when within
sight.
UNavigationSystemV1::GetRandomReachablePointInRadius()


The AI character roams randomly within a defined area. When the player enters its sight range, the
AI stops roaming and begins to chase the player until the player is out of sight, after which it
resumes roaming.

## Output

<img width="880" height="449" alt="Screenshot 2025-11-13 140948" src="https://github.com/user-attachments/assets/74c416e1-692e-4777-aa0a-f89872e05fc9" />
<img width="876" height="748" alt="Screenshot 2025-11-13 141029" src="https://github.com/user-attachments/assets/a1abf0ae-586d-42c7-9d23-d7b48f22a148" />



## Result
The AI character roams randomly within a defined area. When the player enters its sight range, the
AI stops roaming and begins to chase the player until the player is out of sight, after which it
resumes roaming.

