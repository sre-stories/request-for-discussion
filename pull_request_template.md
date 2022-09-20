- [Pull Request Standards for this Repo](#pull-request-standards-for-this-repo)
    - [PR Checklist Template (Only Copy This Into the PR)](#checklist-template)
    - [PR Labels 🏷](#pr-labels)
    - [Purpose of an RFD 📚](#purpose-of-an-rfd)
        - [Structure Info 🏛](#structure)
    - [Naming Standards](#naming-standards)

## Checklist Template
1. Title
2. What problem is this solving?
3. What are the principles and constraints on the design of the solution?
4. How will users interact with these features?
5. What repositories are being changed, if known?
6. What public interfaces are changing?
7. What private interfaces are changing?
8. What is the upgrade impact?
9. What is the security impact?

## PR Labels 🏷
`predraft`
`draft`
`publish`
`abandoned`

## Purpose of an RFD
The following is a way to help you think about and structure an RFD
document. This includes some things that we think you might want to
include. If you’re unsure if you need to write an RFD, here are some
occasions where it usually is appropriate:
Adding new endpoints to an API or creating an entirely new API
Adding new commands or adding new options
Changing the behaviour of endpoints, commands, APIs
Otherwise changing the implementation of a component in a significant way
Something that changes how users and operators interact with the
overall system.
Changing the way that software is developed or deployed
Changing the way that software is packaged or operated
Otherwise changing the way that software is built
This is deliberately broad; the most important common strain across RFDs
is that they are technical documents describing implementation considerations
of some flavor or another. Note that this does not include high-level
descriptions of desired functionality; such requests should instead phrased
as Requests for Enhancement (TBD).

## Structure
##### Title
This is a simple synopsis of the document. Note, the title is not fixed.
It may change as the RFD evolves.
##### What problem is this solving?
The goal here is to describe the problems that we are trying to address
that motivate the solution. The problem should not be described in terms
of the solution.
##### What are the principles and constraints on the design of the solution?
You should use this section to describe the first principles or other
important decisions that constrain the problem. For example, a
constraint on the design may be that we should be able to do an
operation without downtime.
##### How will users interact with these features?
Here, you should consider both operators, end users, and developers. You
should consider not only how they’ll verify that it’s working correctly,
but also how they’ll verify if it’s broken and what actions they should
take from there.
##### What repositories are being changed, if known?
If it’s known, a list of what git repositories are being changed as a
result of this would be quite useful.
##### What public interfaces are changing?
What interfaces that users and operators are using and rely upon are
changing? Note that when changing public interfaces we have to be extra
careful to ensure that we don’t break existing users and scripts.
##### What private interfaces are changing?
What interfaces that are private to the system are changing? Changing
these interfaces may impact the system, but should not impact operators
and users directly.
##### What is the upgrade impact?
For an existing install, what are the implications if anything is
upgraded through the normal update mechanisms, e.g. platform reboot,
sdcadm update, manta-adm update, etc. Are there any special steps that
need to be taken or do certain updates need to happen together for this
##### What is the security impact?
What (untrusted) user input (including both data and code) will be used as part
of the change? Which components will interact with that input? How will that
input be validated and managed securely? What new operations are exposed and
which privileges will they require (both system privileges and Triton privileges)?
How would an attacker use the proposed facilities to escalate their privileges?

## Naming Standards
Each branch should be named with a rfd-{{rfd-number}} example:
rfd-001
Todo:
Look into automating releases for each PR. 



