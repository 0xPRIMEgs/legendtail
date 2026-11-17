# Using Legendtail

Legendtail 0.1.0 is a portable Markdown collection. It has no runtime dependency and no automatic installer. It becomes useful when an agent can read its files alongside a real modeling project.

## In a dedicated asset repository

Place the Legendtail files at the repository root or in a clearly named subfolder. If the repository has no AGENTS.md, the included one can serve as its modeling entry point. If an AGENTS.md already exists, merge a reference to LEGENDTAIL.md into it; preserve existing build, safety, engine, and collaboration instructions.

For example, if the pack lives under `docs/legendtail/`, add this sentence to the existing project instructions:

> For 3D asset creation, editing, and review, read docs/legendtail/LEGENDTAIL.md and its relevant guides. Follow this project's verified rig and export conventions.

Relative links in the pack assume its folders remain together. Copying only AGENTS.md without its referenced files loses the detailed workflow.

## In an ordinary chat

Supply LEGENDTAIL.md, the relevant guide, the asset brief, and the actual references/model. Ask the agent to inspect those materials and perform the requested work. If file reading or modeling tools are unavailable, the agent can prepare a brief or review visible evidence, but should not claim it created a validated 3D asset.

## With other instruction systems

Use your host's documented mechanism for project instructions or file references. This edition does not claim a universal command such as `/legendtail` or install a plugin into any host. The files under `prompts/` are ordinary prompts that can be pasted or referenced.

## A useful first task

Run a narrow repair on a duplicate of a known-good asset: inspect one UV seam, explain the cause, change only its mapping, re-export, and show the actual result. This exercises the brief, source inspection, edit discipline, rendering, and validation without requiring a whole new character.

## GitHub preparation

The top-level README is the landing page. Upload the complete folder to a repository named `legendtail`, or commit it with your usual Git workflow. Review LICENSE.md before publication and adjust the attribution if appropriate. No repository has to be public for an agent to use these instructions. Preparing this folder does not itself create or publish a GitHub repository.
