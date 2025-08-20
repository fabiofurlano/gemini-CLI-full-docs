[Skip to content](https://gemini-cli.xyz/docs/en/tools/web-search#VPContent)

On this page

# Web Search Tool ( `google_web_search`) [​](https://gemini-cli.xyz/docs/en/tools/web-search\#web-search-tool-google-web-search)

This document describes the `google_web_search` tool.

## Description [​](https://gemini-cli.xyz/docs/en/tools/web-search\#description)

Use `google_web_search` to perform a web search using Google Search via the Gemini API. The `google_web_search` tool returns a summary of web results with sources.

### Arguments [​](https://gemini-cli.xyz/docs/en/tools/web-search\#arguments)

`google_web_search` takes one argument:

- `query` (string, required): The search query.

## How to use `google_web_search` with the Gemini CLI [​](https://gemini-cli.xyz/docs/en/tools/web-search\#how-to-use-google-web-search-with-the-gemini-cli)

The `google_web_search` tool sends a query to the Gemini API, which then performs a web search. `google_web_search` will return a generated response based on the search results, including citations and sources.

Usage:

```
google_web_search(query="Your query goes here.")
```

## `google_web_search` examples [​](https://gemini-cli.xyz/docs/en/tools/web-search\#google-web-search-examples)

Get information on a topic:

```
google_web_search(query="latest advancements in AI-powered code generation")
```

## Important notes [​](https://gemini-cli.xyz/docs/en/tools/web-search\#important-notes)

- **Response returned:** The `google_web_search` tool returns a processed summary, not a raw list of search results.
- **Citations:** The response includes citations to the sources used to generate the summary.