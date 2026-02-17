---
title: Why NotebookLM?
description: I built the same AI assistant four different ways before finding the right tool. Here's what I learned.
author: ron
date: 2025-11-01
categories: [ai, notebooklm]
tags: [schh, ai, notebooklm]
media_subpath: /assets/img
image: notebooklm.jpg
published: true
lightbox: false
---

When I started building the SCHH AI Assistant, I knew I wanted something that could answer questions using community documents—not general knowledge from the internet. That requirement narrowed my options, but there were still several ways to approach it. I tried four different frameworks before settling on NotebookLM, and I thought it would be useful to document why.

## The Requirement

Here's what I needed: residents should be able to ask natural language questions about Sun City Hilton Head and get accurate answers drawn from official sources—governance documents, newsletters, club information, and other curated materials. Critically, the system needed to *ground* its responses in those specific documents, not make things up or pull from general AI training data.

This is harder than it sounds. AI models are great at sounding confident even when they're wrong. For a community information assistant, that's unacceptable. If it says the pool hours are 6am-9pm, that needs to come from an actual source document, not the model's best guess based on what's typical.

## The Contenders

I tested four approaches, each with different trade-offs:

### 1. Custom Build with ChatGPT API

**What it is:** Writing my own application using OpenAI's API, implementing Retrieval-Augmented Generation (RAG) to search documents and feed relevant chunks to the model.

**Pros:**
- Complete control over everything—document processing, search logic, response formatting
- Can customize the entire user experience
- Could add features like conversation history, user accounts, analytics
- No platform lock-in

**Cons:**
- *A lot* of work to build and maintain
- Had to handle document parsing, chunking, embedding, vector search, prompt engineering
- Responsible for infrastructure, scaling, error handling
- Cost scales with usage—every query hits the API
- Citation linking requires careful engineering

**Why I moved on:** This would be the right choice if I were building a product or needed specific features not available elsewhere. For a community project I'm running solo, the development and maintenance burden was too high. I wanted to focus on content curation and user needs, not infrastructure.

### 2. ChatGPT Custom GPT

**What it is:** OpenAI's feature that lets you create a specialized version of ChatGPT, upload documents, and give it custom instructions.

**Pros:**

- Very easy to set up—upload files, write instructions, done
- Built-in file handling up to a reasonable size limit
- ChatGPT's interface is familiar to many users
- OpenAI handles all the backend complexity
- Free users can access and use Custom GPTs (as of May 2024)

**Cons:**

- Not embeddable, users are taken to the ChatGPT site and are required to login with an OpenAI (ChatGPT) account
- Limited control over how it searches and retrieves information
- While modest, the hallucination rate was still too high for the level of reliability needed
- Citations are inconsistent—sometimes it references sources, sometimes it doesn't
- Can't customize the interface or embed it elsewhere easily
- Limited document capacity

**Why I moved on:** The inconsistent citations were the main issue—I needed reliable, prominent source attribution. Additionally, while users could access the GPT for free, I'd still need to maintain a Plus subscription as the creator, and I wasn't confident the citation behavior would improve. The lack of control over the retrieval and citation logic made it hard to ensure responses would consistently point back to source documents.

### 3. Chatbase

**What it is:** A platform for building custom chatbots trained on your documents, with options for embedding on websites.

**Pros:**
- Specifically designed for document-based chatbots
- Handles document ingestion and processing
- Embeddable widget for websites (this is a big advantage over the others)
- Can customize branding and behavior to some degree
- Includes analytics and conversation tracking

**Cons:**
- Monthly subscription required (starts around $40/month for meaningful usage and quickly ramps up with usage)
- Limited control over the retrieval and response logic
- Citations exist but are less prominent than I wanted
- Felt like a black box—hard to understand *why* it gave certain answers
- Document limits on lower tiers

**Why I moved on:** I actually used Chatbase for several months and it worked reasonably well. But I kept running into the same issue: when the chatbot gave an answer, I couldn't easily verify where it came from. The citations were there but buried. For a community information tool, I wanted source attribution to be front and center. Also, the ongoing cost added up, and I wasn't sure the platform would evolve in the direction I needed.

## Why NotebookLM Won

**What it is:** Google's AI research tool that creates a personalized AI assistant grounded in your documents. It's designed specifically for document-based conversations.

Here's what made the difference:

### Source Grounding is Built-In

This is the killer feature. Every response in NotebookLM includes inline citations that link directly to the specific passages in your source documents. It's not an afterthought—it's the core design principle. When the assistant says something, you can immediately click through and see exactly where that information came from.

For a community information tool, this is essential. Residents need to trust the answers, and the best way to build trust is to show your work. NotebookLM does this automatically and elegantly.

### NotebookLM Studio Tools

Beyond the basic chatbot, NotebookLM Studio includes some genuinely useful features:

**Audio Overview:** This was a surprise. You can generate a podcast-style conversation between two AI hosts discussing your documents. I created one for the latest SunSations magazine, and it's a completely different way to consume community information—perfect for people who prefer listening while walking or driving. It's also useful for me as a content creator—I can quickly generate audio summaries of new documents.

**Study Guide Generation:** Automatically creates FAQs, briefing documents, and study guides from your sources. Not something I use heavily yet, but interesting for certain types of content.

**Source Management:** Clean interface for adding, removing, and organizing source documents. Can handle PDFs, text files, Google Docs, even YouTube transcripts and web pages.

### The Interface

The NotebookLM interface is rich, with separate panels for the sources, chatbot, and studio tools.  For first-time users this may be a little confusing but once they become familiar with the layout it should be relatively easy to use as the chatbot panel functions like any other AI chatbot.  However, when using the chatbot on a mobile device, selecting and viewing the citation links is a little awkward.  Hopefully the Google Notebook LM team improves this in future versions.

I can share a direct link to the notebook, and anyone with the link can use it. Logging-in with a Google account is needed which add some friction to the process.  Not ideal but also not a deal-breaker right now.  

### It's Free (For Now)

I need to be honest about this: NotebookLM is currently free, and that matters for a community project with no funding. Google has said it will remain free for personal use, but there will eventually be paid tiers for teams and enterprises. For my use case—a single community assistant with public access—I expect the free tier will continue to work.

If that changes, I'll reassess. But for now, not having to worry about usage costs or monthly subscriptions is a significant advantage.

### What It Doesn't Do

To be fair, there are limitations:

**No custom interface:** I can't embed NotebookLM in a custom website or app the way I could my hand-built assistant or the Chatbase chatbot. Users must go to Google's interface and login with their Google account. That's not ideal but was deemed a reasonable tradeoff for this application (experiment), but it might not work for everyone.

**Limited document capacity:** Currently 50 sources per notebook, with size limits per source on the free plan. This can be worked around by combining related documents, but it's a constraint.  The SCHH Knowledge Base has more than 60 documents now and is expected to grow significantly.  Since I'm on their Pro plan my limit is 300 documents.  If I decide to downgrade this in the future I'll need to utilize the aggregation workaround.

**Less control over responses:** I can't fine-tune exactly how it searches or prioritizes information. Google's algorithms make those decisions. Mostly they're good decisions, but occasionally I wish I could adjust the behavior.

**No conversation history across sessions:** Each conversation is ephemeral unless you manually save it. This is not ideal for a user that may want to engage in a long-running conversation over multiple sessions.  Chatbase handled this feature nicely.  Hopefully Google adds some sort of user-based memory and history in future versions.

## The Decision

All-in all, NotebookLM hit the sweet spot: robust source grounding, useful additional tools, zero barrier to entry for users, and manageable for me to maintain. The trade-offs—less customization, some interface constraints—were acceptable given what I gained.

More importantly, it let me focus on the actual work: curating good source documents, organizing information, and helping residents use the tool effectively. That's where I want to spend my time, not on infrastructure and API calls.

## What I Learned

If you're building something similar, here's what I'd consider:

**Start with your requirements:** What's non-negotiable? For me, it was source attribution and ease of access for users. That eliminated several options immediately.

**Think about maintenance:** A custom-built solution might offer more control, but can you realistically maintain it long-term? Solo projects require realistic assessments of your time and interest.

**Consider your users:** Any of the options would have been technically fine, but source attribution is crucial for user trust and acceptance.  NotebookLM was the only one that checks that box, as least as of now.

**Try before committing:** I'm glad I tested multiple approaches. Each one taught me something about what mattered and what didn't.

**Perfect is the enemy of good:** NotebookLM isn't perfect, but it's *good enough* in most of the ways that matter for this project. I wish it was embeddable and more customizable, but it's pretty darn good as it is and more than sufficient for this use.

## Looking Forward

I've been using NotebookLM for the SCHH AI Assistant for a couples months now as an alternative to the primary chatbot interface powered by Chatbase.  I've recently decided to make Notebook LM the primary chatbot and retire the Chatbase and ChatGPT versions.  The source grounding is great—users can verify answers themselves. The audio overview feature also opens up new content possibilities. And I can focus on making the knowledge base better rather than wrestling with infrastructure.

Will I stick with NotebookLM forever? Maybe not. If Google changes the pricing model significantly, or if my needs evolve beyond what it can handle, I'll reassess. But for now, it's the right tool for this job.

I haven't given up on the others, especially Chatbase with its embeddability.  I'm still looking at ways in which a Chatbase-powered chatbot might be easily added to webpages, maybe using a browser extension or bookmarklet.

If you're building something similar and want to talk through the trade-offs, feel free to reach out via the [contact form](/contact). I'm always interested in hearing how others are approaching these problems.

---

*Update: This post reflects my experience as of November 2025. AI tools are evolving rapidly, so some details may change over time.*