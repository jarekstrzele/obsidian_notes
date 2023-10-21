[[_ harvard AI with Python]]

>[!info] SEARCH
>Figure out what to do when we have some sort of situation that the computer is in, some sort of environment that an agent is in and we would like to that agent to be able to somehow look for a solution to that problem 


>[!info] agent
>entity that perceives its environment and acts upon that environment


>[!info] state
>a configuration of the agent and its enviroment
>


>[!info] initial state
>the state in which the agent begins


>[!info] actions
>choices that can be made in a state
>`actions(s)` returns the set of actions that can be executed in state `s`

>[!info] transition model
>a description of what state results from performing any applicable action in any state
>`result(s,a)` returns the state resulting from perfoming action `a` in state `s`


>[!info] state space
>the set of all states reachable from the initial state by any sequence of actions


>[!info] goal test
>way to determine whether a given state is a goal state

>[!info] path cost
>numerical cost associated with a given path

>[!info] SOLUTION
>a sequence of actions that leads from the initial state to a goal state

>[!info] OPTIMAL SOLUTION
>a solution that has the lowest path cost among all solutions


>[!info] **NODE**
>a date structure that keeps track of
> - a state
> - a parent (node that generated this node)
> - an action (action applied to parent to get node)
> - a path cost (from initial state to node)


















