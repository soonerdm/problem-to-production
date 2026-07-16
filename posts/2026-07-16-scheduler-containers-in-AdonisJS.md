# Running AdonisJS Scheduled Jobs in a Separate Docker Container

## The Problem

All users unaware of critical dates that are maintained by a small group of users. Needed an automated system to make everyone aware of these dates. 

## Constraints

- AdonisJS 6 application
- Docker-based deployments
- Local, staging, and production environments
- Shared business logic
- Users not used to getting automated emails
- Staging must not accidentally send production notifications

## Architecture

Scheduler
→ Ace command
→ Service
→ Database and email provider

## Why a Service

Reusable and fired off from scheduler not part of a user action so no need to be in a controller

## Docker Setup

Used a seperate containers for the scheduler and the actual app so that if it needed to be turned off for any reason I can stop the scheduler contianer 


## Problems Encountered

- scheduler new install to this app 
- amd64 image on Apple Silicon - different Dockerfile entries for dev and production
- missing scheduler dependency
- scheduler provider registration
- duplicate scheduler preload
- Docker disk exhaustion
- compiled console entry point in production

## Lessons Learned

