- We currently have social media collection modules. Instagram, facebook, twitter, reddit... Most of them rely on crawling. The plan is to build a task distribution orchestrator, that helps control the flow of the collection across different machines/environments. 
## So for example that orchestrator has a:
- list of machines with their capacities, 
- and a list of credentials. 
## It should:
- receive a task from somewhere (user/admin request...) 
- or generate it (don't worry about the task for now). 
##  It should then 
- examine the resources currently available, with let's say the credentials stored in some database for the platform we're collecting from, and execute the collection task on that machine.
## once the task is done,
- we/orchestrator should be notified about the task 
- and the orchestrator should update it's availability,
- if an error occurs, it should decide what to do (report error, re-execute). 
## further,
- I think what you should do now is try to look up existing similar solutions online and document them, and also think in terms of the technologies you've read about this past week, how it would make sense for you to use them in such an implementation. 
- Keep the orchestration general for now when looking up similar solutions and thinking of your own (overseeing environments and managing any task executions), and we customize later on for our use case. We start with a very simple example in a controlled environment and go from there. 