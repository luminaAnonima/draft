# Appendix: Alignment Evaluation Engine – Interactive Algorithm (v1.3)

*This appendix provides a step-by-step interactive algorithm for evaluating a ripple (action, structure, or design) according to the ethical and metaphysical framework of* The Fabric of Light. *It integrates core rules, scoring logic, qualitative reflection prompts, and usability enhancements for diverse contexts.*

> *This algorithm is derived from the Alignment Evaluation Engine in [/appendix/alignment_engine.md](/appendix/alignment_engine.md). Use them together for full context.*

---

## Overview
This algorithm gathers input across seven foundational principles (R1–R7) to calculate a coherence score, encouraging reflection through prompts and notes. It’s designed for dialogue, supporting individual, team, or community evaluations while respecting cultural and contextual diversity.

---

## Scales
The engine evaluates ripples across the following scales, ensuring multi-dimensional coherence:

- **Personal**: Within one’s self and body (e.g., emotional impact).
- **Interpersonal**: Between people in relational contact (e.g., trust dynamics).
- **Systemic**: Within structures, policies, or institutions (e.g., equity in design).
- **Ecological**: Within the biosphere and non-human world (e.g., environmental impact).
- **Temporal**: Immediate or long-term ripple effects (e.g., sustainability over generations).

---

## Pseudocode: Alignment Evaluation Algorithm
```python
function evaluateRipple():
    print("Welcome. Let's evaluate your ripple for coherence with the field.")
    ripple = input("Describe the ripple (action, decision, design, etc.):")
    scale = input("Select a scale (personal, interpersonal, systemic, ecological, temporal):")

    weights = {
        R1: 0.30,
        R2: 0.20,
        R3: 0.20,
        R4: 0.15,
        R5: 0.15,
        R6: 0.10,
        R7: 0.10
    }

    scores = {}
    total_weighted_score = 0.0
    total_weight = 0.0

    for rule_id in weights.keys():
        rule_name = getRuleName(rule_id)
        prompts = getReflectionPrompts(rule_id, scale)

        print("\nRule:", rule_name)
        for prompt in prompts:
            print("- " + prompt)

        print("Choose a value between 0.0 (not aligned) and 1.0 (fully aligned)")
        while True:
            try:
                score = float(input("Score this rule: "))
                if 0.0 <= score <= 1.0:
                    break
                else:
                    print("Please enter a value between 0.0 and 1.0.")
            except ValueError:
                print("Please enter a valid number.")

        notes = input("Optional: notes or reflections for this rule:")
        scores[rule_id] = { "score": score, "notes": notes }

        weight = weights[rule_id]
        total_weighted_score += score * weight
        total_weight += weight

    final_score = total_weighted_score / total_weight

    if final_score >= 0.85:
        status = "Aligned"
    elif final_score >= 0.65:
        status = "Partially Aligned"
    else:
        status = "Distorted"

    print("\n=== Evaluation Summary ===")
    print("Ripple:", ripple)
    print("Scale:", scale)
    print("Final Score:", round(final_score, 3))
    print("Status:", status)

    for rule_id, data in scores.items():
        print(f"{rule_id}: {data['score']} — {getRuleName(rule_id)}")
        if data['notes']:
            print("  Note:", data['notes'])

    if input("Save this evaluation? (y/n): ") == "y":
        saveEvaluation(ripple, scale, final_score, status, scores)

    return {
        "ripple": ripple,
        "scale": scale,
        "score": final_score,
        "status": status,
        "scores": scores
    }
```

---

## Support Functions
```python
function getRuleName(rule_id):
    return {
        R1: "Resonance Across Scales",
        R2: "Ripple Awareness",
        R3: "Distortion Detection",
        R4: "Intention Tuning",
        R5: "Return Path Integrity",
        R6: "Continuity of Hum",
        R7: "Paradox Holding"
    }[rule_id]

function getReflectionPrompts(rule_id, scale):
    prompts = {
        R1: {
            "default": [
                "Does this action promote flourishing at multiple levels?",
                "Does it avoid control dynamics?",
                "Does it amplify mutual coherence?"
            ],
            "systemic": "[Systemic] Does this policy foster long-term balance across communities?",
            "ecological": "[Ecological] Does it support the biosphere’s health alongside human needs?"
        },
        R2: {
            "default": [
                "Are ripple effects considered beyond immediate gain?",
                "Are marginalized or distant voices included?",
                "Is feedback invited before finality?"
            ],
            "personal": "[Personal] Does this consider emotional impacts on yourself over time?",
            "temporal": "[Temporal] What effects might this have in 10 years?"
        },
        R3: {
            "default": [
                "Does this action isolate or exclude others?",
                "Does it generate imbalance or hoard power/signal?",
                "Does it deny a path for re-entry into resonance?"
            ],
            "systemic": "[Systemic] Does this create inequality ripples in institutions?",
            "ecological": "[Ecological] Does it harm ecosystems without a restoration path?"
        },
        R4: {
            "default": [
                "Is the motive aligned with resonance and integrity?",
                "Does it resist urgency rooted in fear or control?",
                "Is stillness part of its preparation?"
            ],
            "personal": "[Personal] Did you reflect before acting on this?"
        },
        R5: {
            "default": [
                "Can the effect be reversed or repaired?",
                "Does it leave a structure others can use?",
                "Does it complete its cycle responsibly?"
            ],
            "systemic": "[Systemic] Can future users revise or adapt this design?"
        },
        R6: {
            "default": [
                "Does this sustain long-term coherence?",
                "Is the effect persistent but gentle?",
                "Does it echo care beyond its moment?"
            ],
            "temporal": "[Temporal] Does it bridge generations without disruption?"
        },
        R7: {
            "default": [
                "Can the design hold opposites in honest tension?",
                "Is contradiction engaged without denial?",
                "Does synthesis grow from conflict?"
            ],
            "systemic": "[Systemic] Does this policy allow conflicting truths to shape each other rather than cancel?"
        }
    }

    rule_prompts = prompts[rule_id]["default"][:]
    if scale in prompts[rule_id]:
        rule_prompts.append(prompts[rule_id][scale])
    return rule_prompts
```

---

## Sample Run: Evaluating a Personal Decision
**Ripple**: Choosing to take a daily walk in a nearby park.  
**Scale**: Personal

**R1: Resonance Across Scales**  
- Promotes flourishing at personal level and supports public space  
- Score: 0.9  
- Notes: Boosts mood, health, connects indirectly with caretakers of the space

**R2: Ripple Awareness**  
- Considers long-term emotional benefit  
- Score: 0.7  
- Notes: No awareness yet of community accessibility or broader impact

**Final Score**: 0.82  
**Status**: Partially Aligned

---

## Notes
- Scores range from **0.0** (not aligned) to **1.0** (fully aligned)
- This tool does not produce moral judgments; it measures **resonance**
- Notes are vital for insight; use them to deepen collective reflection
- When used in groups, include a facilitator to hold shared inquiry

---

## Future Enhancements
- **Radar Chart Output**: Visual map of R1–R7 coherence
- **Team Sharing**: Export as JSON/CSV for long-term tracking
- **Cultural Layers**: Adapt metaphor sets to local wisdom (e.g., weaving vs. rivers)

---

## Mantra
> To bend, not break.  
> To hum, not shout.  
> To weave, not conquer.  
> To align is to listen.  
> To return is to remember.

