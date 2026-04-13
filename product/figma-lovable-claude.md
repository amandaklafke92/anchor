# Figma vs Lovable vs Claude — Roles & Workflow

## Core Idea
- Figma = clarify structure  
- Lovable = test behaviour  
- Claude = define logic  

---

## Tool Roles

### Figma (Structure)
Use when you need to:
- map user flows
- organise screens
- simplify journeys

Strengths:
- see entire system at once  
- fast iteration (no breakage)  
- easy to restructure  

Output:
→ clear flow + UX decisions  

---

### Lovable (Behaviour)
Use when you need to:
- test interactions
- experience the product
- find what breaks

Strengths:
- real interactions (not simulated)  
- exposes missing logic  
- reveals friction immediately  

Output:
→ working prototype + discovered gaps  

---

### Claude (Logic)
Use when you need to:
- define what happens step-by-step  
- identify edge cases  
- translate flows into instructions  

Strengths:
- turns vague ideas into precise logic  
- fills in missing states  
- improves prompts/specs  

Output:
→ structured logic + detailed behaviour  

---

## How They Work Together

### The Loop

Lovable → Figma → Claude → Lovable  
test → structure → logic → test  

---

### Step-by-Step Workflow

1. Lovable (Start)
- build rough version  
- notice issues (missing steps, confusion, friction)

---

2. Figma (Structure)
- import screenshots  
- map screens left → right  
- label each step  
- simplify the flow  

---

3. Claude (Logic)
- review the flow  
- define:
  - what happens on click  
  - validation rules  
  - error states  
  - transitions  

---

4. Lovable (Test again)
- update prompt/spec  
- rebuild  
- test behaviour  

---

## What Each Tool Solves

| Problem | Tool |
|--------|------|
| “This feels messy” | Figma |
| “What happens here?” | Claude |
| “Does this actually work?” | Lovable |

---

## What Gets Transferred Between Tools

Not code — thinking:

- Figma → structure  
- Claude → logic  
- Lovable → behaviour  

---

## Heuristic

- unclear flow → go to Figma  
- unclear behaviour → go to Claude  
- need to test → go to Lovable  

---

## Key Insight

You are switching between modes:

- Figma = organise ideas  
- Claude = specify ideas  
- Lovable = validate ideas  
