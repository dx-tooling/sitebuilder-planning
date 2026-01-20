# DX·Tooling SiteBuilder

## Project vision and outline

### Introduction

The goal of the SiteBuilder project is to create one or software applications that result in the Web-UI-based SaaS-ification of the landingpages-ai-template project for non-technical people.


### Status Quo

Today, the DX·Tooling organization offers several projects. One of them is `landingpages-ai-template`, a minimalist Node.js-based command line application that enables software engineers to create static (= HTML, CSS, JavaScript, no backend) web pages using LLM-based coding agents like CLaude Code, Windsurf, Cursor, Copilot etc.

It provides two main elements: A Living Styleguide with modern-looking, general-purpose web page elements, and the Node.js based tooling to generate a "dist" bundle of web pages, including dx tooling like linters, a working TypeScript setup, vitest, Webpack, and so on.

The use case for getting from zero to one or more good-looking, technically clean responsive landingpage is very pragmatic and low level: users are expected to clone the repository, load the repository folder into an AI-backed IDE or CLI-based tools like Claude Code, instruct the coding agent to build new source pages, by providing the living styleguide and the Node.js tooling as context, build the source pages into a dist bundle on the command line, and then publish the resulting contents on a web hosting solution of their choice.


### Target status

The goal of the DX·Tooling SiteBuilder project is to allow a "from zero to final web page" process for non-technical users, without the need to deal with git, Node.js, build processes, IDEs etc., by providing a web-based SaaS solution that at its core provides only an LLM-backed chat dialogue interface for user input, and an embedded web page preview for system output.

Under the hood, the SiteBuilder makes use of landingpages-ai-template, its Node.js tooling, git operations (for versioning the work of the end user), and so on, but this is completely encapsulated and opaque to the end user.


### Architecture and Tech Stack outline

The general idea is to build an ETFS-based (Enterprise Tooling for Symfony) Symfony web application, starting off from the etfs-app-starter-kit, backed by a MariaDB SQL database, using the ETFS WebUI bundle and the ETFS Shared Bundle, and thus provide a web-ui that enables all relevant use cases using just a web browser.

The resulting Symfony application will be hosted in a Ubuntu GNU/Linux server environment; the deliverable will be a collection of Docker containers (application, webserver, database).

The developer experience on the CLI will be dominated by the mise-en-place setup as provided by the starter kit, and the dev environment will be provided through the Docker compose setup provided by said starter kit.


### Main features

The new application needs to encapsulate the following core features/use-cases:

- Sign up, sign in, reset password

- Create organization, invite org members, manage org teams and team-member associations

- Configure org-wide bring-your-own-keys for GitHub token (an orgs content projects are versioned as private GH repositories) and LLM API keys

- Create new content project
  - Under the hood, this boils down to creating a new GH repository based off of landingpages-ai-templates, so that the code is available within the site editor, and to enable git-based versioning of the work done on the content project

- Content project editor
  - This provides a chat interface to the user, allowing them to instruct the embedded LLM-based coding agent (which has the landinpages-ai-template git clone plus some system prompts as its context) via a text-to-page-edits approach, and thus modify the content pages via AI, while creating a new version on every round of changes
  - It further provides a preview area, which acts a bit like an embedded browser, allowing the user to see the current state of their content pages
  - It further provides a history feature, allowing the user to revert changes and go back to previous versions of their content pages
  - It further provides an "Export" feature, which allows the user to download a ZIP file containing the dist bundle with the self-contained, serveable HTML/CSS/JavaScript of their content pages


### List of feature verticals

#### Common

#### StaticPages

#### OrgManagement

#### ContentProjectManagement

#### ContentProjectVersioning

#### ContentProjectEditor

#### ContentEditorChat

#### ContentEditorBrowserPreview

#### WorkspaceManagement

#### DockerIntegration

#### LlmIntegration
