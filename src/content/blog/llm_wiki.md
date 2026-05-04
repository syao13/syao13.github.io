---
title: 'Building a personal knowledge base with llm wiki - gene of interest edition'
description: '"You can outsource thinking but not understanding"'
pubDate: '2026-05-03'
heroImage: '../../assets/graph_view.png'
---

The [LLM wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) by Andrej Karpathy has been gaining a lot of traction. The core idea is to use an LLM to incrementally index, organize, query, and maintain a persistent wiki. Unlike a static document dump or a typical RAG setup, the output is a structured, human-readable knowledge base that grows alongside your understanding.

The interesting part is that you're using an LLM to interact with your knowledge base dynamically — not just retrieving answers, but actively reorganizing and extending what's there. Ask a good question, and the answer becomes part of the wiki. The knowledge base compounds.

So I decided to give this a try, using the ACTN3 gene and the rs1815739 variant as an example.

### Collect raw data

To get started, I need to collect some information on the gene first. I started with a Google search and downloaded a few of the top papers. If you already have an existing project with papers, slides, notebooks, etc., just collect everything into a folder.

### Initiate the llm wiki

The original llm-wiki post has clear instructions and enough background information already, which can be directly used by your coding agent as a set of rules. So to start I simply copied the markdown file to the project root folder.

```
ACTN3/
├── raw/
│   ├── xxx.pdf
│   └── ...
└── llm-wiki.md
```

For Claude, run `/init` under the root folder, and Claude easily understood the purpose of the project and rewrote it as a project-specific guideline.

```
ACTN3/
├── raw/
│   ├── xxx.pdf
│   └── ...
├── CLAUDE.md
└── llm-wiki.md
```

### Indexing your initial raw files

After that, run `Ingest` or a more specific prompt in Claude, and you'll get an organized wiki folder with an overview page and relevant entity, source, and concept pages.


```
ACTN3/
├── CLAUDE.md
├── llm_wiki.md
├── folder-structure.md
├── raw/
│   ├── xxx.pdf
│   └── ...
└── wiki/
    ├── index.md
    ├── log.md
    ├── overview.md
    ├── concepts/
    │   ├── xxx.md
    │   └── ...
    ├── entities/
    │   ├── xxx.md
    │   └── ...
    └── sources/
    │   ├── xxx.md
    │   └── ...
```

### Visualize your wiki

[Obsidian](https://obsidian.md/) is what made this wiki feel real. Since the wiki is just interlinked markdown files, you can open the wiki folder as a vault in Obsidian and check the graph view for all the connections between concepts, entities, and sources. 

<div style="display: flex; gap: 1rem;">
  <img src="/assets/obsidian_structure.png" alt="Obsidian folder structure" style="width: 30%; height: 450px; object-fit: contain; object-position: top left;" />
  <img src="/assets/graph_view.png" alt="Obsidian graph view" style="flex: 1; height: 450px; object-fit: contain;" />
</div>

### Enrich your wiki

As you add more documents to the raw folder, have your coding agent `Ingest` again. But the more interesting way to grow the wiki is to `Query` it. Good questions and answers get added back and become part of the knowledge base.

### Summary

LLM makes building the wiki easy, but making sense of what's collected is more crucial than ever. We're not building the tool just to build it — we're building it so we can actually understand the science and push it forward. The LLM can organize and connect the dots, but the understanding still has to come from you.
