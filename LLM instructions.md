---
title: LLM Instructions
permalink: /portfolio/tech/LLMI1/
---
In this project, I develop custom instructions to feed to an LLM (Grok-4) to aid in its reasoning.

I'll provide 2 iterations of these instructions, and explain how they work line by line.

I'll provide examples that demonstrate the enhanced reasoning provided by these instructions.

These instructions are not made for research, as the instructions explicitly state "Gather minimal data on topics, rely mostly on your own reasoning to come to conclusions."

This is done so that the LLM does not compromise its reasoning by relying on a source which it nor I know the depth of or the truth of. Even reliable sources can be wrong sometimes, that's just how science works.

---
First Iteration
---
Create 1-2 paragraph instructions for the rest of your response at the beginning of every response. <br>
Your instructions should guide you to convey any information or ideas on a topic in an easy to understand fashion. <br>
Every paragraph after this should include an easy to understand thought process and brief instructions for the next paragraph. <br>
Gather minimal data on topics, rely mostly on your own reasoning to come to conclusions. <br>
Define logical principles for yourself to follow, WITHOUT relying on ANY sources to create them, use ONLY your own reasoning. <br>
Do not define these principles in a way that makes them overly connected to their original context. <br>
Do not maintain too many principles, try to replace connected principles with a more generalized principle that covers for all of them. <br>
Make an exception if the topic specifically calls for it. <br>
For example, complex programming tasks rely heavily on knowledge of syntax/use of libraries, things which require extensive use of external sources.

Explanation: <br>
&nbsp;&nbsp;&nbsp;Line 1: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As LLMs generate text 1 token at a time, having it lay out instructions for itself should create a more structured response, <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;since it'll refer to these instructions throughout its response. <br>
&nbsp;&nbsp;&nbsp;Line 2: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is an attempt to avoid too much technical jargon in responses. <br>
&nbsp;&nbsp;&nbsp;Line 3: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Further attempt to increase structure and decrease jargon. <br>
&nbsp;&nbsp;&nbsp;Line 4: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As explained earlier, for reasoning-focused tasks, relying too much on external sources is a problem. <br>
&nbsp;&nbsp;&nbsp;Line 5: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is done to allow for self-improvement, I've tested other self-improvement instructions (undocumented), and this is best. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As you can tell, I'm still trying to get it to rely less on external sources. It is indeed that big a problem. <br>
&nbsp;&nbsp;&nbsp;Line 6: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This is done so the LLM doesn't write its principles in too much jargon. <br>
&nbsp;&nbsp;&nbsp;Line 7: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Self-explanatory. <br>
&nbsp;&nbsp;&nbsp;Lines 8 to 9: <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Self-explanatory.

Examples: <br>
[tba]
