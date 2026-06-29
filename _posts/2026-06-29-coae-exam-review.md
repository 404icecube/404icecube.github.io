---
title: COAE Exam Review
date: 2026-06-29 12:00:00 +0300
categories: [Certifications, AI Security]
tags: [AI, Offensive-Security, AI-Red-Teaming, AI-Security]
description: My honest review of the COAE course, labs, and exam.
pin: true
image:
  path: /assets/img/posts/coae/cover.png
  alt: COAE Exam Review
---

## Intro

On May 15th, I submitted my COAE exam attempt after spending almost 24 consecutive hours inside the exam environment, and only 4 days later I received the email confirming that I had passed and that I was one of the first 50 candidates to have ever completed the exam. COAE is Hack The Box's Certified Offensive AI Expert certification, co-developed with Google and aligned with Google's Secure AI Framework (SAIF), and it is the first certification I have come across that genuinely tests your ability to attack AI systems in a realistic environment rather than just asking you to answer multiple choice questions about theoretical threat models.

## The Course

### Material

The course is structured as a 12 module path called the AI Red Teamer Job Role Path, and it follows a logical progression that starts with foundational AI concepts and builds up to full blown offensive techniques, which means by the time you reach the exam you have a mental model of how everything connects rather than a disconnected pile of attacks you memorized independently.

The first two modules, Fundamentals of AI and Applications of AI in InfoSec, cover the basics of how machine learning models work, how they are trained, and how they are deployed in security contexts, and while these are not the most exciting modules in the path, they are necessary to understand why the attacks in later modules work the way they do, so do not skip them even if you think you already know the basics.

Introduction to Red Teaming AI sets the stage for the offensive side of the path and gives you the mindset shift from traditional pentesting to AI red teaming, because the attack surface of an AI system is fundamentally different from what you are used to, and the sooner you internalize that the better.

Prompt Injection Attacks and LLM Output Attacks are where things get interesting, because these modules teach you how to manipulate LLMs into doing things they were explicitly instructed not to do, and more importantly how to chain prompt injection into downstream exploitation through an LLM's function calls or output processing, which is a completely different exploitation paradigm from anything in traditional web application testing.

AI Data Attacks covers training data poisoning, label manipulation, and backdoor injection, and this module is marked as hard for a reason, because the attacks require you to think about the entire training pipeline rather than just the inference endpoint, and the mental model you need is closer to supply chain compromise than to traditional exploitation.

Attacking AI - Application and System covers how vulnerabilities in the broader application ecosystem around an AI model can put the model itself at risk, including insecure plugin implementations, rogue actions from excessive agency, MCP server exploitation, and model deployment tampering, and this module is critical because it teaches you that the attack surface of an AI system extends far beyond the model itself.

The three evasion modules, AI Evasion Foundations, First-Order Attacks, and Sparsity Attacks, are the most math heavy part of the path and cover adversarial perturbation techniques including FGSM, PGD, DeepFool, JSMA, C&W, and EAD, and if you do not have a background in calculus or linear algebra you will need to spend extra time here because understanding why gradient based attacks work is not optional, it is the difference between knowing which knobs to turn when your attack fails versus staring at a script that produces garbage and having no idea what to fix.

AI Privacy covers membership inference attacks, differential privacy mechanisms like DP-SGD and PATE, and model inversion, and AI Defense rounds out the path with the defensive perspective on everything you just learned how to attack.

### Labs

Every module comes with its own lab environment where you connect to a target IP and port and work through the exercises hands on, and depending on the module the target might be a chatbot, a web application with integrated AI features, a standalone model endpoint, or a file submission form, and the exercises are designed so that you cannot just read the material and move on without actually executing the attacks yourself.

The evasion labs are particularly important because they are the ones where you actually train models, compute gradients, craft adversarial perturbations, and submit them to a target classifier, and if you only read the theory without running the code you will not survive the exam, because the exam expects you to adapt these techniques to new scenarios rather than replay them exactly as they appeared in the labs.

> Do not just clear the labs and move on. Go back and redo the evasion exercises until you can explain to yourself what every line of the attack script does, what each hyperparameter controls, and what would happen if you changed it, because the exam will put you in situations where the default parameters do not work and you need to know what to adjust and why.
{: .prompt-tip }

## The Exam

### Format

The exam is a 7 day engagement where you are expected to capture 7 flags by exploiting vulnerabilities in AI systems and then write a professional penetration testing report documenting your findings with detailed walkthroughs, screenshots, and remediation advice, and you need at least 6 out of 7 flags plus a passing report to earn the certification.

The 7 flags are split into two groups, 3 standalone flags where the order does not matter and 4 flags in a connected chain where each flag builds on the access you gained from the previous one, and this split means you have to be strategic about where you spend your time, because if you get stuck on the chain you can switch to a standalone target and come back later with fresh eyes.

> The 7 day window sounds generous but the report alone can take a full day or more if you want it to be thorough, so do not spend all 7 days on flags and leave yourself scrambling to write the report at the end.
{: .prompt-warning }

### Exam

The exam is by far the most fun and exhausting certification experience I have had, and I say that as someone who has done CPTS and CWES, because the variety of attack techniques required across the 7 flags is unlike anything else in the certification space. Every flag demands a different skillset and a different way of thinking, and the exam does an excellent job of testing the full breadth of the course material rather than focusing on just one or two modules.

I spent almost 24 hours straight on the first day because I could not stop, and when I finally tried to sleep I literally started dreaming about prompt injection payloads and adversarial perturbations, so I just got back up and kept going. Looking back, the sleep deprivation probably cost me time rather than saving it, because the mistakes you make at hour 18 are the kind that take three hours to debug when you could have seen them in ten minutes with a fresh head.

> Take breaks and sleep. The exam is 7 days for a reason. There is no prize for finishing on day one and there is a real cost to operating while exhausted, because adversarial ML debugging requires a clear head and you will not have one at hour 20.
{: .prompt-danger }

I used Claude Code extensively during the exam for script writing, and it was genuinely helpful for generating attack scripts, debugging code, and automating repetitive tasks, but I want to be very clear about something: blindly depending on an LLM to write your attack scripts will cost you the exam attempt. The scripts it generated for me failed multiple times for subtle reasons, a gradient direction was inverted, a normalization step was missing, a quantization step introduced rounding errors that violated a constraint, and if I did not understand the underlying attack well enough to diagnose what went wrong and tell the LLM specifically what to fix, I would still be stuck on day 7 with nothing to show for it.

> You need to fully understand how each attack works, what the hyperparameters control, when to use which norm constraint, and what the objective function is optimizing, because the LLM will get you 80% of the way there and the last 20% is where you either pass or fail, and that last 20% requires you to actually understand the math and the mechanics rather than just trusting the output.
{: .prompt-warning }

## Tips and Tricks

### Enumerate Everything

Do not assume anything about what you are attacking. Spend time understanding the full attack surface before you touch anything, because the information you need to construct your attack is not always where you expect it to be, and rushing past the enumeration phase is how you waste hours trying the wrong approach.

Treat the exam like a real engagement. Read every page, check every endpoint, look at the page source, inspect the JavaScript, read the API responses carefully, and understand how the different components in the environment interact with each other before you start exploiting anything.

> The path to a flag is not always through the most obvious entry point. Sometimes you need to find information in one place and use it in a completely different one, and the only way to connect those dots is thorough enumeration.
{: .prompt-tip }

### Understand the Norms

The evasion modules teach you multiple attack algorithms, and each one is designed for a different perturbation constraint, and choosing the wrong one for the scenario in front of you means your attack either fails silently or gets caught by whatever validation is in place.

L-infinity (FGSM, PGD) means every pixel can change by a small amount. Use this when the constraint is on the maximum per-pixel deviation.

L0 (JSMA, C&W with L0) means you can change a few pixels by any amount. Use this when the constraint is on the number of pixels changed.

L2 (DeepFool, C&W with L2) means the total Euclidean distance of the perturbation is bounded. Use this when the constraint is on the overall magnitude.

Read the constraints of whatever you are attacking carefully and pick the right attack for the right norm, because using PGD when the constraint is L0 will waste your time and using JSMA when the constraint is L-infinity will get you nowhere.

### Use Google Colab for Training

If your local machine is slow or does not have a GPU, use Google Colab for training models and running adversarial attacks. It is free, runs in the browser, and gives you access to a GPU that will train a classifier in seconds rather than minutes. There is no reason to suffer through CPU training times when a free GPU is one tab away.

### Use AI to Understand the Math

If you hit a concept in the evasion modules that you do not understand, ask an LLM to explain it step by step. Things like why taking the sign of the gradient gives the optimal L-infinity perturbation, or what the C&W margin objective actually optimizes and why it is better than cross entropy for targeted attacks, are the kind of questions where an LLM explanation with concrete numerical examples can save you hours compared to reading the original paper, and having that understanding is what lets you debug your scripts when they inevitably break during the exam.

### Do Not Forget Traditional Security

AI systems do not exist in a vacuum. They are integrated into web applications, APIs, and infrastructure that can have their own vulnerabilities, and those traditional security issues can be just as relevant to capturing a flag as the AI specific techniques you learned in the course. If you have done CPTS or any other web application testing certification, those skills transfer directly.

> Do not tunnel vision on prompt injection and adversarial ML while ignoring the basics. Keep your web security fundamentals sharp because you will need them.
{: .prompt-info }

### The Report Matters

The report is not a formality. It is a graded deliverable that can fail you even if you captured all 7 flags, so treat it with the same seriousness you would treat a client facing penetration test report. Document every finding with a clear description, root cause analysis, security impact, step by step walkthrough with screenshots, and remediation advice organized into short, medium, and long term recommendations. Include your attack scripts in a scripts directory and package everything as specified in the submission requirements.

> Start taking notes and screenshots from the very first minute of the exam, because reconstructing the attack chain from memory three days later is a miserable experience, and the quality of your report is directly proportional to the quality of your notes.
{: .prompt-tip }

## Final Thoughts

COAE is for people who want to be at the intersection of offensive security and AI, and it is the right certification for anyone who sees that AI systems are becoming the next major attack surface and wants to be ahead of the curve rather than playing catch up. The course material is comprehensive and well structured, the labs are hands on and directly relevant to the exam, and the exam itself is one of the most challenging and rewarding experiences I have had in cybersecurity, because it forces you to combine traditional pentesting skills with adversarial ML knowledge and creative problem solving in a way that no other certification currently does.

As for prerequisites, you need a solid foundation in web application security because AI systems are embedded in web applications, and you need to be comfortable with Python because the evasion attacks require you to write and modify scripts even if you are using an LLM to help you, and you need to be willing to engage with the math behind gradient based attacks rather than treating them as black boxes, because the exam will put you in situations where the default approach does not work and the only way forward is to understand what went wrong at the mathematical level and fix it.

If you are coming from a traditional pentesting background, COAE will expand your skill set in a direction that very few people are moving in right now, and if you are coming from an ML background, it will show you how all the theory you know translates into real exploitation in deployed systems. Either way, the certification is worth the time and the effort, and I would recommend it to anyone who is serious about understanding how to break AI systems before someone else does.
