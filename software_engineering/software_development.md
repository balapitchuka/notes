# Software Development Notes

[toc]




### What is Rapid Prototyping
- Rapid Prototyping involves creating a working model of various parts of the system at a very early stage, after a relatively short investigation.
- The method used in building it is usally quite informal, the most important factor being the speed with which the model is produced.
- The model then becomes the starting point from which users can re-examine their expectations and clarify their requirements
- When this has been achieved, the prototype model is 'thrown away' and the system is formally developed based on the identified requirements.



## Continuous Integration and Continuous Delivery

### What is Devops?

- **It is a philosophy, a set of rules and practices that define a culture that aims to bridge the gap between the development and operation teams**
- The purpose of devops is to facilitate and encourage collaboration between departments

## Automation and Orchestration

- **For**
	- For Developers
	- For IT Operations
	- IT Managers

- **Storyline of Quinn (Systems Administrator)**
	- Problems
		- Overworked
		- Understaffed
		- Backlogged
		- Lots of manual repetitive work
	- Strengths
		- Willingness to learn
		- Passionate about technology
	- Solution found after research
		- Automation

	- Reasons for Learning about Automation
		- Automate routine manual tasks
		- Free up time & reduce workload
		- Unblock backlogged work
		- Focus on more important things

- **What is Automation?**
	- Is a technique, method or system of operating or controlling a process by highly automatic means, **reducing human intervention to a minimum**

- **Types of Automation**
	- Manual
		- Input are entered manually and can be according to our will
	- Scheduled
		- OS Rebot every morning
	- Event Based
		- Harddrive space reaching 90% triggers an automation process to cleanup temporary space
	- Self-Service
		- Inputs are not required from the operator but requires some info
- **Problems Quinn facing after automating many tasks**
	- **Unmanaged automation**
		- What runs where?
		- Who ran what?
		- When did it run?
	- **Uncoordinated automation**
		- How to you connect automation?
	- Solution
		- Implement Orchestration
- **Orchestration**
	- Describes the **arranging** and **coordinating** of automated task.
	- **Orchestration sits on the top of automation**, acting like a conductor for automation, instructing each piece to do its part and then to hand off work when needed to the next piece of automation
- **Why Orchestration**
	- Centralized management
		- What runs where
	- Auditing
		- Who ran what, When it ran
	- Enhanced workflow
		- Orchestration gives you the ability to arrange automation into a sequence. Its the sequence that makes the workflow.
			- Workflow also handles communication between individual pieces of automation in the workflow tying them together into a single process
	- Self-Service Portal
		- Most orchestration tools provides a web frontend for all of your automation

