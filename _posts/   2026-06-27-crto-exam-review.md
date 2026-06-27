---
title: Crto Exam Review
date: 2026-06-27 12:00:00 +0300
categories: [Certifications, Red Team]
tags: [Crto, Red-Team, Cobalt-Strike, Opsec, Active-Directory]
description: My honest review of the CRTO course, labs, and exam.
pin: true
image:
  path: /assets/img/posts/crto/cover.png
  alt: CRTO Exam Review
---

## Intro

On June 22nd, I passed CRTO with a perfect score of 100/100 on my second attempt, which is the result that prompted me to sit down and actually write this review rather than just tweet about it and move on. CRTO is Zero Point Security's flagship red team certification, built around Cobalt Strike and centered on operating inside a monitored, multi domain Active Directory environment, and unlike most certifications in the offensive security space, it takes OPSEC just as seriously as it takes exploitation, which is exactly what makes it stand out from everything else on the market.

## The Course

### Material

CRTO is by far one of the most well organized courses I have done, and the structure follows the natural flow of a real red team engagement rather than presenting techniques as a disconnected list of tricks, so by the time you finish the material, the chain is wired into your head as a sequence rather than as a pile of isolated moves you have to mentally stitch together under pressure.

The topics covered span everything you would expect from a serious red team curriculum, including initial access, situational awareness, host and domain enumeration, privilege escalation, credential theft and dumping, lateral movement, persistence, Kerberos abuse with its full range of delegation and S4U variants, Active Directory Certificate Services attacks, cross domain and cross forest operations, and exfiltration, and each topic is treated with enough depth to actually understand what is happening underneath rather than just memorizing the syntax of the tools.

The videos and written content are straight to the point and easy to follow, with no padding, no filler, and no time wasted on tangents, which is genuinely refreshing compared to most courses in this price range that pad their runtime with restated obvious points and slow walkthroughs of things you could read in two minutes.

### Labs

The labs are stable and should be treated as your playground for practice, because this is where the actual learning happens, and reading and watching the modules only gives you the theory while the labs are where you build the reflexes you will need under exam pressure.

> Lab access resets once every 24 hours, which is a constraint you have to factor into your study schedule from the start, because you cannot simply refresh and try again ten minutes later.
{: .prompt-warning }

The environment itself is a full multi domain Active Directory range, and since the latest CRTO update, Defender is now enabled in almost every single lab, which is a significant change from how the labs used to work and raises the bar considerably, because you are no longer practicing techniques in a sterile environment but against a live EDR that will flag you the moment you reach for the obvious tool or the obvious command. The lab experience is much closer to a real engagement than a CTF, where detections fire, beacons die, and things break for reasons that have nothing to do with whether your exploit is technically correct, which forces you to think about what you are generating, what process you are spawning into, and what your activity looks like to a defender watching the telemetry on the other side.

> Redo the lab chains in multiple different ways, and even repeat the same way multiple times, because the goal is not to clear the lab and move on, but to build muscle memory until executing a clean attack chain without Defender flagging you feels automatic rather than like something you are figuring out in the moment.
{: .prompt-tip }

### What It Taught Me

The single biggest thing CRTO taught me is OPSEC and defense evasion, because before this course my approach to offensive operations was to land a foothold and start running tools, and while I knew which techniques worked, I was not thinking carefully about what each one looked like to the defender on the other side, which is exactly the mindset CRTO sets out to break.

After going through the material and grinding the labs, I now think about telemetry, process behavior, parent child relationships, and detection surface before I touch the keyboard, because every command has a cost in terms of the noise it generates, and CRTO forces you to internalize that cost until you stop asking whether something works and start asking whether it works quietly enough to be worth doing, which is a shift that transfers directly to real engagements, bug bounty work, and any other context where you are operating against active defenses.

## The Exam

### Format

The exam is a 24 hour, pausable exam scored out of 100 points, with the scoring split evenly between two halves so that 50 points are awarded for completing the objectives and 50 points are awarded for OPSEC, and this split is the most important thing to understand about the exam, because it is what makes CRTO genuinely different from almost every other offensive certification on the market.

> You cannot brute force your way to a pass by being operationally successful while making noise, and you cannot pass by being perfectly quiet without actually achieving the objectives, since both halves carry equal weight and you have to deliver on both to walk away with the cert.
{: .prompt-info }

The 24 hour window sounds generous on paper but is tighter than it looks in practice once you factor in breaks, sleep, and the OPSEC discipline the exam demands, although the pausable format helps significantly because it lets you step away when you need to clear your head without burning through your remaining time. You cannot download external tools during the exam, since every tool you need is already provided in the exam environment, which means your job is to know that toolkit cold rather than to bring your own, and this constraint is a feature rather than a limitation because it forces you to actually master the course content instead of leaning on outside utilities you happen to be comfortable with.

### First Attempt

I achieved the objectives in almost 6 hours on my first attempt, which on paper sounds like a strong result, except that operational success is only half the exam, and the half I underperformed on was the OPSEC side, where I lost points for apparent reasons that I should have known before sitting the exam. Looking back at the breakdown, none of the deductions were from techniques I did not know, and every single one was from techniques I knew perfectly well in the labs but executed sloppily under exam pressure, which is the real lesson of the first attempt and the gap between what you know and what you actually do when the clock is running.

Under timed conditions with the objectives in front of you, the temptation is always to fall back on the fastest tool you know rather than the quietest one, and you end up making decisions in seconds that you would never make if you stopped to think for thirty more, because people make stupid mistakes under pressure that they would never make in the labs, and CRTO is no exception to that rule no matter how prepared you think you are walking in.

> Before executing any command or any step, think twice about how it could be noisy and how it could be flagged, because the exam is 24 hours for a reason, there is no prize for finishing early, and there is a real penalty for rushing.
{: .prompt-danger }

### Second Attempt

After receiving the grading breakdown from my first attempt, I sat down and went through every single instance where I had lost points, and for each one I traced the deduction back to the specific decision I made in the moment, identified the cleaner alternative I should have reached for instead, and refined my approach in the labs until executing the clean version felt automatic, and I retook the exam 7 days after the first attempt to walk away with a perfect score of 100/100.

Two things were critical for the second attempt, and the first is breaks, because breaks are mandatory rather than optional, the exam is pausable for a reason, and that reason is that no human being can operate at peak attention for 24 hours straight, so stepping away to eat something, sleep if you need to, and come back fresh is how you catch the mistakes that would otherwise cost you points, and you should treat the pause button as a tool rather than as a luxury you can do without.

> Build a personal OPSEC cheatsheet by opening the ZPS course material, hitting <kbd>Ctrl</kbd> + <kbd>F</kbd> for every instance where Rastamouse mentions OPSEC, and compiling those notes into your own reference organized by attack phase. This is the single most useful artifact you can build during prep, because it turns the exam into an exercise in following your own playbook rather than improvising one in real time.
{: .prompt-tip }

## Tips and Tricks

This section is the collection of small habits and technique level decisions that separated my first attempt from my second, written at the technique level without any exam specifics, so you can apply them in the labs and have them ready by the time you sit down for the real thing.

### Process Selection and Spawnto

When you are operating in a user context and running .NET tooling or anything in the Rubeus family, set your `spawnto` to the full literal path of `werfault.exe` rather than letting the default ride, because the default spawnto choices are exactly the ones that have been beaten to death in EDR detection rules, and werfault is a process that defenders are conditioned to ignore in normal volume.

When you are operating in SYSTEM context and running anything that touches LSASS such as sekurlsa, lsadump, or DCSync, swap your spawnto to `svchost.exe`, because SYSTEM context operations spawning from non SYSTEM looking parents are one of the loudest patterns you can generate, and svchost makes the activity blend into the normal flood of service host noise that nobody is going to investigate without a specific reason.

> Always use the full literal path for `spawnto_x64`, not the sysnative alias, because the sysnative path resolution can introduce inconsistencies in how the process is recorded in telemetry.
{: .prompt-tip }

### Spawnto vs ak-settings Spawnto

It is worth understanding that the normal `spawnto` command and the `ak-settings` spawnto configuration are not interchangeable, even though they both deal with which process your beacon spawns into. The normal `spawnto` command is the global setting on your beacon that controls which process Cobalt Strike spawns when it needs a temporary process to host post exploitation activity such as fork and run operations, and it applies to anything triggered from that beacon going forward until you change it again.

The `ak-settings` spawnto, on the other hand, applies specifically to the lateral movement primitives that build on top of the service control manager and similar mechanisms, and configuring it controls the process that gets spawned on the remote side as part of the jump itself rather than on the local side as part of a fork and run. If you set the normal spawnto carefully but never touch ak-settings before jumping, you can end up with a clean local execution context and a noisy remote one, which is one of the easier ways to lose OPSEC points without realizing why.

> Configure your `ak-settings` spawnto before any service based lateral movement, because the default values will generate command lines that are immediately recognizable on the remote host, and the deduction will show up in your OPSEC score even though your local execution looked clean.
{: .prompt-warning }

### Lateral Movement

Use `scshell` for jumps wherever it is appropriate, because it abuses an existing service rather than creating a new one, which keeps your activity inside the normal service control footprint of the host rather than generating a brand new service creation event that any default detection rule will flag immediately. Combined with a properly configured ak-settings spawnto, scshell is one of the quietest lateral movement options you have available without leaving the course toolkit.

### Enumeration

Prefer `ldapsearch` over `powerpick powerview` whenever the data you need is reachable through raw LDAP queries, because powerpick still has to host PowerShell content in memory and that comes with all the AMSI and ScriptBlock telemetry that PowerShell based tooling generates, while a clean LDAP query is just protocol traffic to a domain controller that blends into the normal authentication and lookup chatter of any AD environment.

> PowerView is comprehensive, but its comprehensiveness is exactly what makes it loud, so reach for it only when the query you need genuinely cannot be expressed as an LDAP search, and treat raw LDAP as your default enumeration primitive.
{: .prompt-tip }

### Execute-Assembly Discipline

Default to BOFs over `execute-assembly` whenever a BOF equivalent exists, because execute-assembly spawns a new process to host the .NET runtime and that new process is exactly what EDR is watching for, while BOFs run inline in your existing beacon process and generate a fraction of the telemetry.

> When `execute-assembly` is genuinely unavoidable, route it through a proxied session rather than firing it directly from your sensitive beacon, so that if something does flag it, the detection burns a sacrificial context rather than your foothold.
{: .prompt-warning }

Avoid running Rubeus through execute-assembly, since the static signatures on Rubeus binaries are well known and Defender will catch the assembly the moment it lands in memory, so prefer BOF based ticket operations or upload the kirbi file and use ticket use primitives instead of running the full assembly.

### AppLocker

> Spend serious time on the AppLocker challenge in the labs until you can clear it without thinking, because AppLocker bypass is one of those skills that is impossible to fake under pressure, and being smooth on it in the exam saves you both time and OPSEC points.
{: .prompt-tip }

### Exam Hygiene

Enumeration is the entire game, and you should resist every temptation to act before you understand the environment, because every action you take blind is an OPSEC risk you did not need to take, and the operators who score perfectly are the ones who spend two hours mapping before they spend two minutes attacking.

Take notes the entire time you are in the exam, including every command you ran, every host you touched, every ticket you extracted, and every credential you recovered, because your future self at hour eighteen will not remember what your past self at hour three did, and the notes are also what you fall back on if you have to retry a step or backtrack from a dead end.

> Save every Kerberos ticket you generate or extract, because tickets are reusable, regenerating one costs time you may not have, and a ticket you already have in hand is one less authentication event you have to make against a DC.
{: .prompt-tip }

After you escalate to SYSTEM, inject into a SYSTEM context svchost rather than into explorer or any other interactive process, because injecting into an interactive process while SYSTEM creates parent child relationships that immediately stand out in telemetry, and svchost keeps your SYSTEM activity inside the part of the process tree that nobody investigates by default.

## Final Thoughts

CRTO is for people who are genuinely interested in offensive security and red teaming rather than in collecting another certification to hang on the wall, and it is the right course for anyone looking to advance their Active Directory skills while taking evasion seriously, as well as for anyone who wants to get comfortable with the real world C2 practices that an actual engagement demands rather than the sanitized version you get from most courseware. As for prerequisites, a solid grasp of Active Directory is sufficient to start, since you do not need prior red team certifications, years of offensive security experience, or a memorized copy of the MITRE ATT&CK matrix, and what you actually need is a working understanding of how AD environments are structured, how authentication flows work, and what concepts like delegation and trusts mean, because if you have that foundation, CRTO will take you the rest of the way, and if you do not, build that foundation first and come back, because either way the course is worth every dollar and every hour you put into it.