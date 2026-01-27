+++
date = '2026-01-27T14:45:54-05:00'
draft = false
title = 'Recent Website Enhancements: Lab Console, Search, and Man Pages'
categories = ['Development', 'Updates']
tags = ['Website', 'Updates']
+++

## Overview

Over the last few days, I've been focusing on bringing a more "Industrial Lab" and terminal-centric feel to the MickTheLinuxGeek website. This dev log summarizes the last three major updates merged into the codebase.

## 1. Dynamic Lab Console & Custom 404 Page (PR #3)

The first major update introduced a dynamic **Lab Console** component. This component is designed to emulate a terminal-like interface directly on the home page, providing an interactive feel from the moment a visitor arrives.

Along with the console, I implemented a custom **404 page** (`404.html`). Instead of a generic error message, visitors who get lost will now see a themed recovery screen that fits perfectly within the site's aesthetic.

## 2. Technical Polish: Search & RSS (PR #4)

Visibility and accessibility were the focus of the fourth pull request. I added a dedicated **Search functionality** (`content/search.md` and `layouts/_default/search.html`), making it easier to find specific posts and content across the site.

Additionally, I integrated an **RSS CTA** partial. This call-to-action encourages readers to subscribe to the feed, ensuring they never miss an update from the "Lab."

## 3. Unix/Linux Style "Man" Page (PR #5)

In keeping with the Linux enthusiast theme, the latest update (PR #5) adds a **Unix/Linux style "Man" page**. Built with `content/man.md` and a custom layout in `layouts/_default/man.html`, this page provides documentation and site info in the familiar manual format that every terminal user knows and loves.

---

*Stay tuned for more updates as I continue to refine the digital lab environment!*
