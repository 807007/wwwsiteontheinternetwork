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
&nbsp;&nbsp;&nbsp;The following is an attempt to make Grok-4 (with the instructions) write a text-rendering program in processing 4.3 (sept. 29):
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
[tba]

