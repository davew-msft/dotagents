# Fabric AI-assisted development notes

## Links

* [Fabric skills](https://github.com/microsoft/skills-for-fabric)
* for Fabric:  fabric-ai-toolkit


## Fabric Apps

* [docs](https://learn.microsoft.com/en-us/fabric/apps/)
* [create an app with ghcp](https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot)
* [good docs](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/from-prompt-to-production-whats-new-in-fabric-apps/5369134)
* use the Rayfin plugin and your coding agent gets guidance matched to the SDK version.  
  * the Universal App template:  agent turns a prompt into a deployable project quickly.  
* [repo](https://github.com/microsoft/rayfin)
* [Fabric Apps Gallery](https://community.fabric.microsoft.com/category/pbi_comm_galleries/discussions/pbi_fabricappsgallery)

## Project Osmos

You can describe transformation logic in natural language, and an AI coding assistant will happily generate hundreds of lines of Spark code.

The idea behind Project Osmos is simple: instead of asking AI to help you write data engineering code, you define a complete problem and the outcome you expect. It has the autonomy to use the tools and an orchestration framework to build, validate, troubleshoot, and refine its implementation, making decisions within the boundaries you set and working towards a high quality output.

Under the hood, Project Osmos uses a purpose-built orchestrator that coordinates multiple specialized agents to tackle the problem. Each agent has a well-defined role from code generation to validation to evaluation.  The goal isn't to remove humans from the process. It's to let the agents take on the investigation and implementation work, while allowing people to guide the outcome, resolve ambiguities, and review the evidence.

Steps:
* Install [Fabric Skills](https://github.com/microsoft/skills-for-fabric):  `npm install -g @github/copilot`
* ask ghcp/coding agent to "create a project osmos task"
* choose your workspace/LH, describe the outcome you want, specify how you'd like the results to be validated.  

Example:  

```text

Use Project Osmos to build a medallion architecture in the Fabric workspace Sales Analytics and the lakehouse SalesLakehouse. Read the customer, order, order-line, and product files under Files/landing, but do not modify or delete the original files.

Create Bronze Delta tables that preserve the source data and include ingestion timestamps and source-file names. In Silver, standardize data types, remove duplicate customers and products using their business keys, reject orders without a valid customer, quarantine malformed records, and join order lines to the corresponding orders and products.

Create Gold tables for daily sales, customer sales, product performance, and monthly revenue by customer segment. Save separate notebooks for loading Bronze, transforming Silver, and building Gold, and design them so they can be safely rerun without creating duplicate records.

Run the notebooks in the correct order. Validate row counts between layers, business-key uniqueness, referential integrity, null customer and product identifiers, rejected-record counts, and source-to-Gold revenue totals. Do not promote the Gold tables unless the validation checks pass, and provide a summary of the resulting tables, notebooks, rejected records, and validation results.

```

demo:  https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started
video:  https://www.linkedin.com/posts/andrzejstrzala_microsoftfabric-dataengineering-aiagents-ugcPost-7518001621499453440-JAIo/
The current public Osmos quickstart uses supported command-line clients as the entry point, including GitHub Copilot CLI, Claude Code, and Codex.:  https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started   The user creates a managed task associated with a Fabric lakehouse and monitors its progress in Fabric. 
video:  around 52 min:  https://www.youtube.com/watch?v=imLQIl3XiDg
capabilities:  https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview
capacity consumption:  https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-consumption

Links:

* [Quickstart](https://learn.microsoft.com/fabric/data-engineering/data-engineering-agent-get-started)
* [Docs](https://learn.microsoft.com/fabric/data-engineering/data-engineering-agent-overview)
* [Best Practices](https://learn.microsoft.com/fabric/data-engineering/data-engineering-agent-best-practices)