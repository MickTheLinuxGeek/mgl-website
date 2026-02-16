+++
date = '2026-02-15T14:38:55-05:00'
draft = false
title = 'February 2026 Dev Log: DITS GraphQL & Data Portability'
categories = ['Dev Log']
tags = ['DITS', 'GraphQL', 'Homelab', 'Self-Hosting', 'BuildInPublic']
+++

Halfway through February, and the focus remains heavily on the technical core of the Developer Issue Tracking System (DITS). We've moved from the UI refinements of January into the heavy-duty backend infrastructure and data ownership features that define the project's philosophy.

## DITS: GraphQL Backend Completed

The biggest milestone this month is the completion of the **GraphQL backend infrastructure**. While we had REST endpoints early on, migrating the core logic to a unified GraphQL schema has drastically simplified the communication between the frontend and the data layer.

- **Type-Safe Schema**: Leveraging TypeScript across the stack means our GraphQL types directly map to our database models and frontend props.
- **Efficient Queries**: Reduced over-fetching on the Kanban board view, leading to even snappier load times.
- **Improved Extensibility**: Adding new features (like the Area management we worked on last month) is now a matter of extending the schema rather than writing custom REST handlers.

## Data Portability: Ownership First

A primary goal for DITS is that the user owns their data. To support this, I've begun implementation of the **data-export feature**.

This tool allows users to export their entire issue history, labels, and metadata as a standardized JSON/CSV bundle. It ensures that DITS never becomes a "data silo"—if you decide to move your workflow elsewhere, your history moves with you.

## Homelab Bonus: Jellyfin Migration

Outside of DITS development, I've been doing some "spring cleaning" in the lab.

- **Hardware Upgrade**: Migrated the Jellyfin media server from its aging host to a new **HP ProDesk G4 mini**.
- **Performance Gains**: The new hardware provides much better hardware transcoding support, making for a much smoother experience on mobile devices and remote viewing.

## What's Next?

With the GraphQL foundation solid, I'll be shifting my attention toward the desktop integration and further expanding the data-export capabilities into more formats.

Stay tuned for more updates as we continue building in public!
