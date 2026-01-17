# DX·Tooling SiteBuilder

## Project vision and outline

### Introduction

The goal of the ETFS SiteBuilder project is to create one or software applications that result in the Web-UI-based SaaS-ification of the landingpages-ai-template project for non-technical people.

### Status Quo

Today, the DX·Tooling organization offers several projects. One of them is `landingpages-ai-template`, a minimalist Node.js-based command line application that enables software engineers to create static (= HTML, CSS, JavaScript, no backend) web pages using LLM-based coding agents like CLaude Code, Windsurf, Cursor, Copilot etc.

It provides two main elements: A Living Styleguide with modern-looking, general-purpose web page elements, and the Node.js based tooling to generate a "dist" bundle of web pages, including dx tooling like linters, a working TypeScript setup, vitest, Webpack, and so on.

The use case for getting from zero to one or more good-looking, technically clean responsive landingpage is very pragmatic and low level: users are expected to clone the repository, load the repository folder into an AI-backed IDE or CLI-based tools like Claude Code, instruct the coding agent to build new source pages, by providing the living styleguide and the Node.js tooling as context, build the source pages into a dist bundle on the command line, and then publish the resulting contents on a web hosting solution of their choice.

### Target status

The goal of the DX·Tooling SiteBuilder project is to allow a "from zero to final web page" process for non-technical users, without the need to deal with git, Node.js, build processes, IDEs etc., by providing a web-based SaaS solution that at its core provides only an LLM-backed chat dialogue interface for user input, and an embedded web page preview for system output.

Under the hood, the SiteBuilder makes use of landingpages-ai-template, its Node.js tooling, git operations (for versioning the work of the end user), and so on, but this is completely encapsulated and opaque to the end user.
