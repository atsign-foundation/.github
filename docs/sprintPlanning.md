# **Overview:**
Sprint planning is core to how we plan and operationalize our development work at Atsign. In this README, you will find our current process and best practices that we use for sprint planning. Continuous improvement is fundamental to our process, so this document is considered a living, breathing document.  Check back for updates.

If you are leading a sprint for the team, you will find here useful information and context for what we do, how we do it, and why we do it. Sprint plans are run every 2 weeks, with the caveat of holidays - the schedule is subject to change.

## **Key links, documents, and repositories:**
- [Github Kanban Project Board](https://github.com/orgs/atsign-foundation/projects/8/views/142 "Github Kanban Project Board") 
- [Burndown Report](https://docs.google.com/document/d/1eAMJioRg7bF5DB9TZlIvBWBWdyf9tbzoUEzkKNFHDLk/edit "Burndown Report")
- [Parabol Retrospective](https://action.parabol.co/meetings "Parabol Retrospective")
- [Archived retros and sprint plans](https://drive.google.com/drive/u/1/folders/110cPNpH_BGumHz2oKhCuAFi2baxrKwc7 "Archived retros and sprint plans")
- [MASTER Capacity plan ](https://docs.google.com/spreadsheets/d/1mEEgdK1cB_OFT3cO8nonjUqufCQRqJLqNl8KWHTPIfM/edit#gid=1598336825 "MASTER Capacity plan ") 
- [.csv dump card instructions](https://docs.google.com/document/d/1gyEE9t9BGn8-VgeVM6gl32yFWYLW58dbndD5p-8xj8Y/edit ".csv dump card instructions")
- [Planning Poker](https://play.planningpoker.com/login "Planning Poker")

### **Last update to our process:**
In **January of 2023** we transformed our sprint planning with the following:
A better review process for the backlog.
A special view to help speed up planning poker.
Architecture call items now use the “Discussion” type instead of a priority tag
Removed the need for core and app kanban columns, instead using project and type
We now use GitHub iterations for managing PRs
SPs are loaded in real-time and totaled as they are added eliminating post-planning clean-up

Sprint planning enhancements were gathered and socialized across the team. The goal is to streamline how we sprint plan while providing deeper visibility and easier cross-functional teaming.

### **The Basics:**
**Story points (SP’s):**
Our approach has evolved to pre-estimating story points when the ticket description has a clear context of the work involved. Whoever picks up the issue can easily understand the work involved. We are now nimble at translating our capacity to story points for an array of work. For newbies, story point translations can be found here.

**Triage:**
As you’re adding items, be sure to add the priority, label(s), and story points if you have a solid idea of the work involved.  Please ensure ticket descriptions are fairly easy to understand and you can speak to the work involved during planning poker if we are estimating.  If you don’t know, I would ask if the ticket is premature and does it require further vetting by the team in an Arch call.

**Backlog:**
A good rule of thumb for adding items to the backlog is a well-defined project or task where you have a really good idea of the work, which the description reflects. Like this bug ticket, Gary created. Or this enhancement Chris put on the backlog. 

Aging issues, missing descriptions, and issue context is currently where we have a gap. Deciding how long something should stay on the backlog, as well as missing descriptions requires further team discussion in an Arch call so we can address this.

**Planning Poker:**
This is where we spend the time talking through a well-defined issue that we don’t know how much time or work is involved. We tap into tribal knowledge and best guesses. We then come to a team agreement on story points for the work.

**Arch Call (Discussion):**
A newly created priority on the backlog for fleshing out projects and eng tasks where we may not be able to create a well-defined ticket or you simply have a brilliant idea you’d like to propose. This will allow us to create undefined tickets that can become meaningful tasks or projects.

### **Sprint Planning Process:**
We follow a four-step process for organizing our sprints: 
1. Plan
2. Categorize 
	- *The ‘categorize’ activity is new to the process. There are two fields that aid in categorizing tasks. (Project & Type)*
4. Prioritize
5. Poker

### Sprint Planning Prep Checklist:
In order to save time on PR sprint planning call, we go through individual tickets that are still in the current PR and either:
- move them to the next PR then adjust SP to what you think is remaining 
- or change status from Active to Backlog or forward ticket to next PR
- or whatever the appropriate action is
- and add an explanatory comment if required
- and the newly added deadline column we can use for revenue related activities
 
This link will show you your tickets that are still in current PR and not Backlog or Closed https://github.com/orgs/atsign-foundation/projects/8/views/139?filterQuery=pr%3A%40previous+assignee%3A%40me+-status%3ABacklog%2CClosed+
 
### Day before sprint planning:
- Put ideas into the [retrospective](https://action.parabol.co/meetings "retrospective") 
- Update your capacity for the current PR in the [master capacity](https://docs.google.com/spreadsheets/d/1mEEgdK1cB_OFT3cO8nonjUqufCQRqJLqNl8KWHTPIfM/edit#gid=873712221 "master capacity") planner
	- Check the ready box to indicate completion
- Update the [burndown report](https://docs.google.com/document/d/1eAMJioRg7bF5DB9TZlIvBWBWdyf9tbzoUEzkKNFHDLk/edit "burndown report")
- [Planning Poker](https://play.planningpoker.com/login?returnUrl=%2Fdashboard "Planning Poker") for current tasks that require team discussion and review
