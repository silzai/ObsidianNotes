# project crashing
## background
- we can use PERT and CPM to plan, control project schedule in terms of duration
- but in reality, when we start working, we may be requested to **reduce** the duration of the project, but we planned nicely before for longer duration
- if we manage to reduce durations of activities on the critical path, then we can reduce the total duration, to do that we can:
	1) pick the critical activity that will cost the least to reduce the duration
	2) when we reduce a duration for an activity, then the critical path will change, and cost may increase (because of putting more resources on the activity to reduce duration of)
	3) then repeat the above steps iteratively until you reach the desired duration of the project
## steps
- max crash duration: $$max \ crash \ duration = ND - CD$$
- $$CC-NC$$
- Slope (crash cost per duration): $$\frac{CC-NC}{max \ crash \ duration}$$
- select the activity with the *least* slope (cost per duration), and reduce the cost for *that* activity.