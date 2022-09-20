# Standards for an RFD
- [PR Checklist Template (Only Copy This Into the PR)](#checklist-template)
- [PR Labels 🏷](#pr-labels-)
- [Purpose of an RFD](#purpose-of-an-rfd)
- [Details 📚](#details-)
	- [Title](#title)
    - [What problem is this solving?](#what-problem-is-this-solving)
    - [What are the principles and constraints on the design of the solution?](#what-are-the-principles-and-constraints-on-the-design-of-the-solution)
    - [How will users interact with these features?](#how-will-users-interact-with-these-features)
    - [What repositories are being changed, if known?](#what-repositories-are-being-changed-if-known)
    - [What public interfaces are changing?](#what-public-interfaces-are-changing)
    - [What private interfaces are changing?](#what-private-interfaces-are-changing)
    - [What is the upgrade impact?](#what-is-the-upgrade-impact)
    - [What is the security impact?](#what-is-the-security-impact) 
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
`predraft` - A single individual contributor is working on a POC/concept. </br></br>

`draft` - The concept is ready to be discussed with a sqad or team. </br></br>

`publish` - Team feedback has been collected and any diviations from the orginal concept are documented in the PR. Once reviews and approvals are docunented, merge into main.</br></br>

`abandoned` - Team feedback was contructive and determined this RFD was not the best path forward. The reason for abandonment is clearly documented/stated to avoid being resurfaced wihout factor changes. </br></br>

## Purpose of an RFD
> The following is a way to help you think about and structure an RFD
> document. This includes some things that we think you might want to
> include. If you’re unsure if you need to write an RFD, here are some
> occasions where it usually is appropriate:
> Adding new endpoints to an API or creating an entirely new API
> Adding new commands or adding new options
> Changing the behaviour of endpoints, commands, APIs
> Otherwise changing the implementation of a component in a significant way
> Something that changes how users and operators interact with the
> overall system.
> Changing the way that software is developed or deployed
> Changing the way that software is packaged or operated
> Otherwise changing the way that software is built
> This is deliberately broad; the most important common strain across RFDs
> is that they are technical documents describing implementation considerations
> of some flavor or another. Note that this does not include high-level
> descriptions of desired functionality; such requests should instead phrased
> as Requests for Enhancement (TBD).

</br>

## Details 📚</br>
#### Title 
> This is a simple synopsis of the document. Note, the title is not fixed.
It may change as the RFD evolves.



#### What problem is this solving?
> The goal here is to describe the problems that we are trying to address
that motivate the solution. The problem should not be described in terms
of the solution.



#### What are the principles and constraints on the design of the solution?
> You should use this section to describe the first principles or other
important decisions that constrain the problem. For example, a
constraint on the design may be that we should be able to do an
operation without downtime.



#### How will users interact with these features?
> Here, you should consider both operators, end users, and developers. You
should consider not only how they’ll verify that it’s working correctly,
but also how they’ll verify if it’s broken and what actions they should
take from there.



#### What repositories are being changed, if known?
> If it’s known, a list of what git repositories are being changed as a
result of this would be quite useful.



#### What public interfaces are changing?
> What interfaces that users and operators are using and rely upon are
changing? Note that when changing public interfaces we have to be extra
careful to ensure that we don’t break existing users and scripts.



#### What private interfaces are changing?
> What interfaces that are private to the system are changing? Changing
these interfaces may impact the system, but should not impact operators
and users directly.



#### What is the upgrade impact?
> For an existing install, what are the implications if anything is
upgraded through the normal update mechanisms, e.g. platform reboot,
sdcadm update, manta-adm update, etc. Are there any special steps that
need to be taken or do certain updates need to happen together for this

#### What is the security impact?
> What (untrusted) user input (including both data and code) will be used as part
of the change? Which components will interact with that input? How will that
input be validated and managed securely? What new operations are exposed and
which privileges will they require (both system privileges and Triton privileges)?
How would an attacker use the proposed facilities to escalate their privileges?

</br>


## Naming Standards
Each branch should be named with a `rfd-{{title}}-{{rfd-number}}` 
> *Example:*</br>   `rfd-aws_provider_update_001`


</br>


# Standards for an RFE
## RFE definition

> An RFE is the request for additional functionality to the system, with the emphasis on requirements rather than design -- it is the "what" than the "how". RFEs should almost always result in the addition of user- or operator-visible abstraction, with the exception being an existing abstraction that is to be enhanced in some quantifiable way. A good RFE needs to answer two questions: what problem needs to be solved (and why?) and what defines success?

#### "What needs to be solved?"

> There is an art to describing the problem that needs to be solved: too vague, and one runs the risk of putative solutions that don't actually solve the problem; too specific and the problem description drifts into a solution description. Ideally, the problem description should be abstract and yet still sufficiently concrete to constrain (but not overly constrain!) solutions. For example, an RFE asking for a GPGPU-based container offering (say) is vague and likely underspecified -- but one asking for an offering based on NVIDIA Tesla P100 GPUs may be too confining. Rather, the RFE may be for GPGPU-based container offering that allows for CUDA-based workloads that can economically compete with a p2-8xlarge AWS instance (say). Or perhaps it's even higher level than that: an offering that allows for optimal execution of specific frameworks like PyTorch, Theano and TensorFlow. Or perhaps the RFE phrases the problem at its most general ("we need GPGPU-based instances") and provides specific use-case detail to convey an understanding of the solution space.

#### "Why?"

> Engineers are problem solvers -- and understanding why a problem needs to be solved it very much helps to understand the implications in terms of what needs to be solved. Sometimes the "why" of a problem only helps to motivate its solution (or the engineer providing it!), but in some cases the "why" can shape the solution significantly -- or imply other problems that need to be solved.

#### "What defines success?"

> It's important to know the least that can be done to be considered successful -- not because engineers are underachievers, of course, but rather to allow for an iterative course to be plotted. This is an exercise in defining the minimum viable product: at what point is the problem considered to be sufficiently solved to at least allow further feedback? Alternatively, it may be that emphasis is not on "minimum" but "viable": many pieces of software infrastructure require significant work to render something that is at all usable, and the emphasis may be on the high level of functionality required to meet even the lowest of expectations.
</br>

# RFEs in contrast
#### To better understand an RFE, it can be helpful to contrast it to other similar (but distinct!) concepts.

## RFEs vs. RFDs
> RFEs will tend to be shorter, vaguer, and more speculative than RFDs. There will be projects that have both an RFE and an RFD: the RFE describing what is desired, the RFD describing the mechanism that satisfies that desire and how it is built. There will also be projects that have an RFE but no matching RFD -- namely, those that are not implemented, or for which the implementation is so straightforward as to not merit a separate RFD. Finally, there will be projects that have an RFD but no corresponding RFE -- especially if they pertain to improvements to the implementation or architecture of the system that do not extend or modify its abstractions. Note that this implies an unfair assymetry: RFDs may freely discuss the "what", but RFEs should really refrain from specifying the "how". The implication here is that engineering-originated discussion will often (though not always) better fit as an RFD than an RFE -- and certainly where that discussion centers on improving how it works or how it's built rather than expanding what it does.


#### Todo:
Look into automating alot of this 


#### Credit:
Credit where credit is due - mostly created if not entirely from https://github.com/TritonDataCenter/rfd 
