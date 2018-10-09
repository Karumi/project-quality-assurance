# Agile Delivery - Karumi Methodology 

## Overview

At Karumi we used a variation of Scrum focused on quality and deliverability we called that Agile Delivery.

Why don’t we directly apply Scrum? Scrum implementation we have seen have the Product Owner, QA or the developer validating of items in the sprint backlog. In our implementation of agile the customer is the one marking the items as Done. Based on our experience customers do not work at the same pace as we do. We could have some sprint with no item feedback and other Sprint validating various sprint items. That's why the Sprint in Agile Delivery does contain the item validation. Besides that, Sprint as the concept of a set of Increments that will be presented during the Demo. This clashes with the modern cycle of continuous delivery and asynchronous communication. For this reason, each increment in Agile Delivery has his async demo. The forms we use are a screenshot, a video, a testing environment or any combination of these elements.

Agile Delivery is a framework for managing product development and delivery. A fundamental principle is a recognition that the product has an amount of unknown. These unknowns can go from product definition to technical challenge to face. Not everything can be known in advance or tested prototyping. Accepting that the problem cannot be fully understood or defined up front. So instead, we focus on how to maximize the team's ability to deliver quickly and often. The goal is to optimize the workflow to gather feedback as soon as possible and having the possibility to iterate on it. That also includes responding to emerging requirements and adapting to evolving technologies.

Four roles have emerged in practice that serves particular purposes.

* [The Customer](#The-Customer)
* [The Product Owner](#The-Product-Owner)
* [The Scrum Master](#The-Scrum-Master)
* [The Development Team](#The-Development-Team)

The best way to describe the lifecycle of the Agile Delivery is via the feedback loops involved.

* [Strategy Review (Quarterly)](#Strategy-Review-(Quarterly))
* [Priority Review (Quarterly/Monthly)](#Priority-Review-(Quarterly/Monthly))
* [Sprint(Weekly)](#Sprint(Weekly))
* [Replenishment(Weekly)](#Replenishment(Weekly))
* [Sprint Planning(Weekly)](#Sprint-Planning(Weekly))
* [Daily Scrum(Daily)](#Daily-Scrum(Daily))
* [Delivery - Increment Review(Weekly-Continuous)](#Delivery---Increment-Review(Weekly-Continuous))

## Roles

Here below are listed the roles that will be actively involved. An important reminder is that these are describing roles, not job descriptions. One person can take on more than one role, and these can vary in a project basis or even during the lifetime of a project.

### The Customer

The customer is responsible for the following:

* Describe the functionalities that the development team will produce.

* Define the priority of each item in the product backlog.

* Define the acceptance criteria of each feature. The acceptance criteria defined will be used to validate the increments produced.

* Define the non-functional requirements.

### The Product Owner

The product owner manages the product backlog to achieve the desired outcome that the customer seeks to do.

This role exists to address challenges like unclear priorities or lack of understanding of the business. Depending on the project this role is assumed by someone from Karumi or our client.

### The Scrum Master

The scrum master ensures the team lives agile values, principles and follows the processes and practices agreed.

The role does not have any actual authority, and anyone from the development teams can take the responsibility. A difference from the general implementation of Scrum, this is not a job by an individual.

### The Development Team

The development team consists of the people who deliver the product increment inside a Sprint.

The primary responsibility of the development team is to deliver the increment that delivers value every Sprint. How the work is divided up to do what is left and is up to the team to determine based on the conditions at that time.

## Feedback loops

Feedback loops are here to define the structure in a timeline of a project. These do not correspond to meetings. They are the steps to follow to gather enough information to plan and deliver. 

### Strategy Review (Quarterly)

We do an estimation of features defined by the customer at the following times:

* Before starting a project.

* At each milestone.

* Every three months if it is a long-running project.

Working-day is the unit we use for estimation. Also, we provide an estimated date of delivery based on resources availability. These pieces of information help the customer define budgets and priorities.

### Priority Review (Quarterly/Monthly)

Based on the size of the project and the team, this feedback can be gathered from quarterly to monthly. The product owner will sit with the customer and review the priorities of the features. This phase uses the information gathered from the Strategy Review, and Feedback gathered during each Sprint.

### Replenishment (Weekly)

The product owner or each developer based on priorities provided by the customer will prepare the sprint planning.

### Sprint(Weekly)

A Sprint is a timebox of one or two weeks during which the team produces a shippable increment. The team itself define the timebox at the beginning of the project and adapt it if needed.

### Sprint Planning (Weekly)

Sprint Planning occurs in two parts. In the first part, the product owner and the rest of the team agree on which product backlog items the Sprint will contain. The Product Owner will remind the product goal that will everybody focus the tasks of the Sprint on it. If the team is small and know wells the set of features, this part is done during the Sprint Planning meeting. If not, it's prepared in advance to be ready to review during the sprint planning meeting. Also, all items from the previous Sprint Backlog that are not finished will be added to this Sprint Backlog.

In the Second Part of Sprint Planning, the team determines how they will deliver the identified product backlog items.  The team may identify specific tasks necessary to make that happen if that is one of their practices.  The product backlog items identified for delivery and tasks if applicable, make up the Sprint Backlog.

Once the development team and product owner establish the scope of the Sprint, no more items can be added to the Sprint Backlog. This protects the team from scope changes within that Sprint.

### Daily Scrum (Daily)

The Daily Scrum is a short (limited from 5 to 15 minutes) discussion where the team coordinates their activities for the following day. The Daily Scrum is not intended to be a status reporting meeting with each member reporting progress to the same person but to each other. Also is the place to raise problems and issues and reserved time after the daily meeting with the corresponding people to solve them.

### Delivery - Increment Review(Weekly-Continuous)

As soon as the increment is in a reviewable state, the customer reviews it. The purpose is to demonstrate and give the customer access to the increment to get feedback. Feedback from the increment review gets placed into the Product Backlog for future consideration.

Delivery for Review can be available from multiples times a day up to once a week depending on the deliverable platform and features.

## Artifacts

### Product Backlog

The product backlog is an ordered list of all the possible changes that could be made to the product. The Product Owner maintains the product backlog on an ongoing basis including its content and order.

### Sprint Backlog

The Sprint Backlog is the collection of product backlog items selected for delivery in the Sprint. And the tasks identified by the team necessary to deliver those product backlog items and achieve the Sprint Goal.

### Increment

The increment is the collection of the Sprint Backlog Items that meet the team’s Definition of Ready for Delivery by the end of the Sprint. 

### Definition of Ready for Delivery - Increment Review

The definition of Ready for Delivery is a team’s shared agreement on the criteria that a Sprint Backlog Item must meet before it is considered done. We generally include automated tests, pull request, manual validation by the development team.

## What Scrum do that we don't or do differently?

Our sprint planning meeting is at most an hour. The content for the Sprint Backlog should be proposed in advance by the development team or product owner. Every member of the development team should have enough information understand the items of Sprint Backlog item.

We don't do scrum poker or even state the size of each item. We assign to each developer, and we discuss if there is enough time to fit into the timebox that is a Sprint.

We do daily scrum if the development team is bigger than two developers, but we don't force it to be in person or through video conference. Daily scrum is fine if asynchronous and by group chat. The goal is to coordinate the team and spot possible impediment and can be achieved independently of the medium. As we work remotely, we sometimes use the daily scrum as a social channel to be able to communicate daily by voice/facial expression. Besides that, we do continuous communication through group chat.

There is no figure of scrum master. Everyone in the team should be aware of the rules we follow, and only if needed someone from the team will remind the steps we follow.

If any impediment is found it is the same developer with the collaboration of the Product Owner that will take ownership and find solutions to it.

There is no sprint review meeting. If planned work was not completed during the sprint and no priority has changed, it will put in the next Sprint Backlog.

We don't do demos as a meeting. Instead, as soon as the work is ready for delivery, we publish it and assign it to the stakeholder for review. This process can include screenshots or video if the feature allows it.

Our definition of Done is different from the one from Scrum; ours is defined by Ready for Delivery + Customer Accepted.

We don't do Sprint retrospective. Our process is continuous, and every team member is responsible for the Scrum methodology. If any improvements need to be done on the process, it will be communicated with the team as per need basis.

We do project Post-Mortem, were we list: What went well? What could be improved? And Action that can be taken based on this.

We don't do burndown chart or measure velocity. We are not interested in the speed of the team, but instead, if the feature can be delivered to the expectation, we communicated with the customer. The difference is that we focus if we are in the budget or on time. 

## Conclusion

Agile Delivery emerges from our experience as professional working in product-focused companies and years now operating as a consultancy. Our goal is to be able to be agile in a world where we keep in mind that the resources are limited and shipping beats perfection. 

The culture at Karumi is what we do, not what we say we do.

## References

* What is Scrum? [https://www.scrum.org/resources/what-is-scrum](https://www.scrum.org/resources/what-is-scrum)

* Kanban [https://www.agilealliance.org/glossary/kanban/](https://www.agilealliance.org/glossary/kanban/)

* Scrum [https://www.agilealliance.org/glossary/scrum](https://www.agilealliance.org/glossary/scrum)

* Scrumban [https://www.agilealliance.org/what-is-scrumban/](https://www.agilealliance.org/what-is-scrumban/)