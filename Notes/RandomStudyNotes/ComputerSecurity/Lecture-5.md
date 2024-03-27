# Contents
1) RBAC
2) ABAC
# RBAC
# Role
- role comes with set of tasks
- task is subset of role
- session: mapping between individul
- example: TA has 3 tasks as a role,
	- reading lab
	- teaching lab
	- uploading material on blackboard
	- TA role has the privilege of
## Role Hierarchies
- can do inheritance in and with roles 
## Windows Groups
- Groups have no privilege directly, but are associated with the roles
- they are user related
# ABAC
- attribute based access control
- every object in the world has an attribute
- 3 types of things whose attributes decide whether the authorization engine does "permit or "deny":
	- User
	- Environment
	- Information Asset
>[!info]
>This means that even if you provide correct credentials, there still may be denial of entry if any other attribute is not present