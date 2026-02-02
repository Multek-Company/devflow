# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

DevFlow is a collection of Claude Code plugins designed to be easily downloaded into Claude Code repositories to enhance development workflows during vibe coding sessions. Each plugin is a self-contained unit that extends Claude Code's capabilities.

## Architecture

This is a greenfield project. The architecture should be established as development begins. Key design decisions to make early:

- Plugin format and structure (how each plugin is packaged)
- Installation mechanism (how users add plugins to their repos)
- Plugin discovery and registry (how users find available plugins)
- Configuration schema (how plugins are configured per-project)
