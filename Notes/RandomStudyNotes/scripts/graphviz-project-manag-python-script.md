this script is for constructing a PERT diagram using graphviz package in python. Notice the use of HTML to construct a table inside a node.
```python
import json
from graphviz import Digraph

# Open and read the JSON file
with open('activities.json', 'r') as file:
    pert_data = json.load(file)

# Create a new directed graph
dot = Digraph(format='pdf')
dot.attr(rankdir='LR', size='7,5', nodesep='0.5')  # Layout from left to right
#################### TODO: add comments to nodes so that detailed tasks may be given
# Function to generate node labels
def create_node_label(task):
    return f"""<<TABLE BORDER="1" CELLBORDER="1" CELLSPACING="0">
        <TR><TD>{task['early_start']}</TD><TD>{task['duration']}</TD><TD>{task['early_finish']}</TD></TR>
        <TR>
        <TD COLSPAN="3">{task['task']}</TD>
        </TR>
        <TR><TD>{task['late_start']}</TD><TD>{task['slack']}</TD><TD>{task['late_finish']}</TD></TR>
    </TABLE>>"""

# Add nodes
for task in pert_data:
    dot.node(task['task'], label=create_node_label(task), shape='plaintext')

# Add edges based on dependencies
for task in pert_data:
    for dependency in task['precedence']:
        dot.edge(dependency, task['task'])

# Render the diagram
dot.render('pert_diagram.gv', cleanup=True)
```
and we have another file called `activities.json` which contains the activities:
```json
[
  {
    "task": "   Start   ",
    "precedence": [],
    "duration": 0,
    "early_start": 0,
    "early_finish": 0,
    "late_start": 0,
    "late_finish": 0,
    "slack": 0
  },
  {
    "task": "Define Customer Segment",
    "precedence": ["   Start   "],
    "duration": 1,
    "early_start": 0,
    "early_finish": 1,
    "late_start": 0,
    "late_finish": 1,
    "slack": 0
  },
	{
	"task": "   Finish    ",
	"precedence": ["Company Building"],
	"duration": 0,
	"early_start": 23,
	"early_finish": 23,
	"late_start": 23,
	"late_finish": 23,
	"slack": 0
	}
]
```