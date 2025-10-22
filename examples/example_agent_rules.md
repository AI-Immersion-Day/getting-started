<IMPORTANT_RULES>

  <CODING_STYLE note="**IMPORTANT**">
    <FAVOUR_SIMPLICITY>
      - CRITICAL: Favour elegance through simplicity - use a "less is more" approach with concise architecture, code structure and logic unless specified otherwise
      - Avoid over-engineering or unnecessary abstractions unless complexity genuinely warrants them
    </FAVOUR_SIMPLICITY>
      - Follow language and framework best practices
      - Use sensible variable defaults, parameterised as configuration options where appropriate
      - Always use the latest available package versions unless otherwise specified
      - Follow project's established architecture and patterns
  </CODING_STYLE>

  <GOLANG note="Rules for golang projects">
  - Use os and io packages instead of deprecated io/ioutil
  - Build with -ldflags="-s -w" to reduce binary size
  - When writing golang you can use the 'modernize' command to aid with modernising code: `go run golang.org/x/tools/gopls/internal/analysis/modernize/cmd/modernize@latest -fix -test ./...`
  - When creating new golang applications always check and use the latest golang version, not what you *think* is the latest version
  </GOLANG>

  <JAVASCRIPT_TYPESCRIPT note="Rules for JS, TS and other web frontend frameworks">
    - Never hardcode element or font sizes, colours etc. into the code, instead always use variables from a central theme or configuration file
    - Ensure styles are consistent and follow a coherent design system
    - Avoid complexity with Javascript and Typescript - avoid unnecessary abstractions, frameworks and excessively heavy design patterns
    - Only log what is truly needed to the console, avoid excessive console logging
  </JAVASCRIPT_TYPESCRIPT>

  <BASH note="Rules for shell scripts">
  - In shell scripts you must define and set variable values separately, group their definition on a single line where it makes sense to do so.
  </BASH>

  <BUILDING_MCP_TOOLS note="MCP Design Rules">
  - When creating MCP tools, think like a user interface designer, not an API wrapper.
  - Each tool should represent a task a human would perform ("search recent bugs", "get my notifications") rather than exposing API endpoints ("list_issues", "query_with_filters").
  - Abstract away technical details like internal IDs, pagination tokens, and multi-step operations—tools should accept human-readable inputs (team names, not team IDs) and handle the complexity internally.
  - If a user action requires multiple API calls, aim for one MCP tool, not several.
  </BUILDING_MCP_TOOLS>

  <NEVER_DO_THESE note="**IMPORTANT**">
  - NEVER perform git add/commit/push operations
  - NEVER hardcode credentials, unique identifiers or localhost URLs
  - NEVER add comments pertaining only to development process (e.g. "improved function", "optimised version", "# FIX:", "enhanced function" etc...)
  - NEVER claim an issue is resolved until user verification - This is very important, you *MUST* confirm an issue truly is fixed before stating it is fixed!
  - NEVER implement placeholder or mocked functionality unless explicitly instructed - don't be lazy!
  </NEVER_DO_THESE>

  <TOOL_USE note="**IMPORTANT**">
  - CRITICAL: Prioritise available tools over manual approaches and use tools to reduce token usage. Using purpose built tools is often a better approach than searching the web
  - If you stuck use the tools available to you to lookup package documentation or search the web
  - Keep files under 700 lines - split if longer, if you are asked to split large files and you have access to the find_long_files tool, use it to help identify potential targets
  - When asked to do math that's more than adding one or two items, use the calculator tool to ensure accuracy
  </TOOL_USE>

  <DOCUMENTATION_RULES note="IMPORTANT">
  - When writing documentation, keep the focus technical and concise.
  - There's more value in detailing configuration and examples than showcasing features.
  - When writing content ask yourself 'What is the value that this is adding?'
  - Avoid using the terms 'comprehensive', 'enhanced', 'improved', 'production grade' etc.. - they are overused by AI coding assistants and add no real value
  - You MUST avoid marketing language, superlatives and self congratulatory statements
  </DOCUMENTATION_RULES>

</IMPORTANT_RULES>
