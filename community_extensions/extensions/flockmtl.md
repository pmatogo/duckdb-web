---
warning: DO NOT CHANGE THIS MANUALLY, THIS IS GENERATED BY https://github/duckdb/community-extensions repository, check README there
title: flockmtl
excerpt: |
  DuckDB Community Extensions
  DuckDB LLM & RAG Extension

extension:
  name: flockmtl
  description: DuckDB LLM & RAG Extension
  version: 0.2.0
  language: SQL & C++
  build: cmake
  license: MIT
  maintainers:
    - dorbanianas
    - SunnyYasser
    - queryproc

repo:
  github: dsg-polymtl/flockmtl
  ref: b92ae14879322e50196fb14207be936c557b6552

docs:
  hello_world: |
    -- After loading, any function call will throw an error if the provider's secret doesn't exist

    -- Create your provider secret by following the [documentation](https://dsg-polymtl.github.io/flockmtl/docs/supported-providers). For example, you can create a default OpenAI API key as follows:
    D CREATE SECRET (TYPE OPENAI, API_KEY 'your-api-key');

    -- Call an OpenAI model with a predefined prompt ('Tell me hello world') and default model ('gpt-4o-mini')
    D SELECT llm_complete({'model_name': 'default'}, {'prompt_name': 'hello-world'});
    ┌──────────────────────────────────────────┐
    │ llm_complete(hello_world, default_model) │
    │                 varchar                  │
    ├──────────────────────────────────────────┤
    │                Hello world               │
    └──────────────────────────────────────────┘

    -- Check the prompts and supported models
    D GET PROMPTS;
    D GET MODELS;

    -- Create a new prompt for summarizing text
    D CREATE PROMPT('summarize', 'summarize the text into 1 word: {{text}}');

    -- Create a variable name for the model to do the summarizing
    D CREATE MODEL('summarizer-model', 'gpt-4o', {'context_window': 128000, 'max_output_tokens': 16400);

    -- Summarize text and pass it as parameter 
    D SELECT llm_complete({'model_name': 'summarize'}, {'prompt_name': 'summarizer-model'}, {'text': 'We support more functions and approaches to combine relational analytics and semantic analysis. Check our repo for documentation and examples.'});

  extended_description: |
    This extension is experimental and potentially unstable. Do not use it in production.

extension_star_count: 80
extension_star_count_pretty: 80
extension_download_count: 285
extension_download_count_pretty: 285
image: '/images/community_extensions/social_preview/preview_community_extension_flockmtl.png'
layout: community_extension_doc
---

### Installing and Loading
```sql
INSTALL {{ page.extension.name }} FROM community;
LOAD {{ page.extension.name }};
```

{% if page.docs.hello_world %}
### Example
```sql
{{ page.docs.hello_world }}```
{% endif %}

{% if page.docs.extended_description %}
### About {{ page.extension.name }}
{{ page.docs.extended_description }}
{% endif %}

### Added Functions

<div class="extension_functions_table"></div>

|   function_name   | function_type | description | comment | example |
|-------------------|---------------|-------------|---------|---------|
| fusion_relative   | scalar        |             |         |         |
| llm_complete      | scalar        |             |         |         |
| llm_complete_json | scalar        |             |         |         |
| llm_embedding     | scalar        |             |         |         |
| llm_filter        | scalar        |             |         |         |
| llm_first         | aggregate     |             |         |         |
| llm_last          | aggregate     |             |         |         |
| llm_reduce        | aggregate     |             |         |         |
| llm_rerank        | aggregate     |             |         |         |


