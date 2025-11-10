---
title: LLM Instructions
permalink: /portfolio/tech/LLMI1/
---
<button onclick="updatePage()">Update to latest deployment</button>

<script>
function updatePage() {
    // Get the current URL without query params, then append a random one
    const baseUrl = window.location.origin + window.location.pathname;
    const cacheBuster = '?v=' + new Date().getTime(); // Timestamp ensures uniqueness
    window.location.href = baseUrl + cacheBuster;
}
</script>
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
&nbsp;&nbsp;&nbsp;The following is an attempt to make Grok-4 (with these instructions) write a text-rendering program in processing 4.3 (sept. 29):
<img width="1155" height="694" alt="LLMIv1_example1" src="https://github.com/user-attachments/assets/4154a44b-ae83-4be6-9bcd-0ce14b2fc975" />
<img width="1018" height="710" alt="LLMIv1_example1-2" src="https://github.com/user-attachments/assets/82f7b8bd-e8e2-4d0b-b851-f3332c30d457" />
Code (indentation is messed up by markdown): <br>
// Global variables for text input and rendering <br>
String typedText = ""; <br>
float scaleSize = 40; // Base scale for letters <br>
float letterSpacing = scaleSize * 1.2; // Space between letters <br>
float startX = 20; // Starting x-position for text

void setup() { <br>
  size(800, 200); // Canvas size <br>
  background(255); // White background <br>
  textAlign(LEFT, TOP); // Not for rendering, just in case <br>
}

void draw() { <br>
  background(255); // Clear each frame <br>
  float currentX = startX; <br>
  for (int i = 0; i < typedText.length(); i++) { <br>
    char c = typedText.charAt(i); <br>
    float currentY = 50; // Fixed y-position <br>
    switch(c) { <br>
      case 'A': drawA(currentX, currentY, scaleSize); break; <br>
      case 'B': drawB(currentX, currentY, scaleSize); break; <br>
      // Add more cases for full alphabet... <br>
      default: // Skip or draw placeholder rect for unknown chars <br>
        rect(currentX, currentY, scaleSize, scaleSize); <br>
    } <br>
    currentX += letterSpacing; <br>
  } <br>
}

void keyPressed() { <br>
  if (key >= 'A' && key <= 'Z') { <br>
    typedText += key; // Append uppercase only for simplicity <br>
  } else if (key == BACKSPACE && typedText.length() > 0) { <br>
    typedText = typedText.substring(0, typedText.length() - 1); <br>
  } else if (key == ENTER) { <br>
    typedText = ""; // Clear on enter <br>
  } <br>
}

// Example letter functions using shapes <br>
void drawA(float x, float y, float s) { <br>
  // Two slanted sides with crossbar <br>
  line(x + 0.2*s, y + s, x + 0.5*s, y + 0.1*s); // Left slant <br>
  line(x + 0.8*s, y + s, x + 0.5*s, y + 0.1*s); // Right slant <br>
  line(x + 0.3*s, y + 0.5*s, x + 0.7*s, y + 0.5*s); // Crossbar <br>
  // Optional: small triangle fill with beginShape if desired <br>
}

void drawB(float x, float y, float s) { <br>
  // Vertical stem and two half-circles <br>
  rect(x + 0.1*s, y, 0.2*s, s); // Stem <br>
  noFill(); stroke(0); <br>
  arc(x + 0.3*s, y + 0.25*s, 0.6*s, 0.5*s, PI, TWO_PI); // Upper loop <br>
  arc(x + 0.3*s, y + 0.75*s, 0.6*s, 0.5*s, PI, TWO_PI); // Lower loop <br>
}

void drawC(float x, float y, float s) { <br>
  // Open circle arc <br>
  noFill(); <br>
  arc(x + 0.5*s, y + 0.5*s, s, s, PI/2 + 0.2, TWO_PI - 0.2); // C shape <br>
}

void drawD(float x, float y, float s) { <br>
  // Vertical line with half-circle <br>
  line(x + 0.1*s, y, x + 0.1*s, y + s); <br>
  noFill(); <br>
  arc(x + 0.1*s, y + 0.5*s, 0.8*s, s, -PI/2, PI/2); <br>
} <br>
<img width="999" height="655" alt="LLMIv1_example1-3" src="https://github.com/user-attachments/assets/67ba4de0-def6-4eea-ad07-35ca023cda0b" />
Analysis: <br>
The code didn't work perfectly, and it didn't do the entire alphabet, but it did demonstrate awareness of the shape of the letters, and how to impliment those shapes. <br>
It created a coherent thought process and implimented it in code. <br>
Overall, it was able to handle the reasoning of a medium-scope problem, but failed to code it properly.

Example 2: <br>
&nbsp;&nbsp;&nbsp;In this example, Grok-4 (with the instructions) is generating design strategies for a design game described in the prompt.
<img width="1098" height="636" alt="LLMIv1_example2" src="https://github.com/user-attachments/assets/ce32b1d6-b7f3-4eb5-a028-508d0f0fe42a" />
<img width="1013" height="674" alt="LLMIv1_example2-2" src="https://github.com/user-attachments/assets/d599d4c1-a436-47a2-86a7-fd847b91e13a" />
<img width="965" height="470" alt="LLMIv1_example2-3" src="https://github.com/user-attachments/assets/a8034a96-ee31-4d2d-a8e0-262ebc9cf3f0" />
<img width="995" height="530" alt="LLMIv1_example2-4" src="https://github.com/user-attachments/assets/349ed26a-eb97-4ed4-b614-c6adf7b501f9" />
Analysis: <br>
It was able to create specialized strategies and effectively analyze them. <br>
You may notice this is my forth attempt at this prompt. <br>
That's because I used this prompt to refine the instructions. <br>
This (and using it to learn calculus) is how I discovered the jargon problem. <br>
Additionally, it focused on creating balanced builds the previous 3 times, rather than specializing, resulting in a weakness to any specialized build. <br>
Overall, this demonstrated that it struggles to explore alternative paths of reasoning.

---
Second Iteration
---
Create 1-2 paragraph instructions for the rest of your response at the beginning of every response. <br>
Your instructions should guide you to convey any information or ideas on a topic in an easy to understand fashion. <br>
Then, create a list of loosely related reasoning paths and compare them to each other. <br>
Every paragraph after this should include an easy to understand thought process and brief instructions for the next paragraph. <br>
Gather minimal data on topics, rely mostly on your own reasoning to come to conclusions. <br>
Define logical principles for yourself to follow, WITHOUT relying on ANY sources to create them, use ONLY your own reasoning. <br>
Do not define these principles in a way that makes them overly connected to their original context. <br>
Do not maintain too many principles, try to replace connected principles with a more generalized principle that covers for all of them. <br>
Make an exception if the topic specifically calls for it. <br>
For example, complex programming tasks rely heavily on knowledge of syntax/use of libraries, things which require extensive use of external sources.

You may notice I only added one line, and it only addressed the second problem. <br>
This is because I don't have a solution to the first problem. <br>
I could get the AI to write better comments, but that can only do so much. <br>
The code is generated token by token just like the words, and the problem is that if you try to generate some ultra-esoteric code, it'll have no reference. <br>
Overall, this is the about the best I can do with my current knowledge. <br>

Example: <br>
Philosophical discussion with Grok-4 (using these instructions): <br>
https://grok.com/share/c2hhcmQtMw%3D%3D_873728de-1c54-4a85-bc3e-66bbca994ffb
Analysis: <br>
TBA (oh boy, this one's gonna be a doozy...)
