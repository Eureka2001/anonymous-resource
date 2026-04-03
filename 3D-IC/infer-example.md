## Input

```
You are an expert in robot manipulation and navigation. Your task is to analyze the feasibility of each candidate plan for successfully completing the given instruction. You will provided with the task instruction and some candidate interaction plans, where each plan includes a sequence of observations and the specific actions to be executed at the corresponding locations.

The task instruction: Move tomato from cabinet to counter
Candidate interaction plans: 

plan_1: Navigate at <3D tokens>, Pick at <3D tokens>, Navigate at <3D tokens>, Place at <3D tokens>.
plan_2: Navigate to <3D tokens>, Pick at <3D tokens>, Navigate at <3D tokens>, Place at <3D tokens>.
plan_3: Navigate to <3D tokens>, Pick at <3D tokens>, Navigate at <3D tokens>, Place at <3D tokens>.
plan_4: Navigate to <3D tokens>, Pick at <3D tokens>, Navigate at <3D tokens>
plan_5: Navigate to <3D tokens>, Pick at <3D tokens>, Navigate at <3D tokens>

For observations corresponding to the "navigate to tomato", consider:
- If the tomato is not visible, the likelihood that the surroundings indicate it is nearby.
- If the tomato is visible, proximity to the object and readiness for grasping.

For observations corresponding to the "pick tomato", consider:
- Visibility and clarity of the tomato for grasping.
- Accessibility of the object without occlusion or obstruction.
- Suitability of the current angle and position for reliable grasping.

For observations corresponding to the "navigate to counter", consider:
- If the counter is not visible, the likelihood that the surroundings indicate it is nearby.
- If the counter is visible, suitability of the current position for placement.

For observations corresponding to the "place at counter", consider:
- Obstacles or clutter that could make placement difficult.
- Stability of the object if placed here.
- Suitability of the current angle and position for placement.

Evaluate the feasibility of each interaction waypoint based on the above criteria, and then combine these evaluations to determine an overall score for each plan.

Please provide a concise reasoning summary that compares all candidate plans. Then assign a raw feasibility score (a continuous value between 0.0 and 1.0) to each plan. Output your evaluation strictly in valid JSON format only, with no extra explanation or natural language outside the JSON structure.
{
    "reason": "<Concise explanation comparing the plans and justifying the scores>",
    "plan_1": <score_1>,
    "plan_2": <score_2>,
    "plan_3": <score_3>,
    "plan_4": <score_4>,
    "plan_5": <score_5>
    "answer": <plan_ID>,
}
```

## Output


```
{
  "reason": "Plan_3 is the most feasible overall, with strong waypoint quality across all stages. The poses in Plan_3 provide a grasping position that is closer to the target object and free of occlusion, as well as a placement pose that is better aligned with the counter. The poses in Plan_1 approaches the counter from its shorter side, which is more likely to cause the object to slip or fall. The counter area in Plan_2 is cluttered, making it less suitable for placement. The scene in Plan_3 looks like a bathroom, leading to a low likelihood that a counter is nearby, while the scene in Plan_4 appears to be a spacious living room, where finding a counter is still possible, but not very likely.",
  "plan_1": 0.6,
  "plan_2": 0.9,
  "plan_3": 0.5,
  "plan_4": 0.1,
  "plan_5": 0.3,
  "answer": "plan_3"
}
```
