# AI Article Rectification Challenge

Solution Approach
Overview
The objective was to improve the article rectification process by enabling fact verification against the original source article. Previously, the system performed rectification using only the AI-generated article. The updated implementation retrieves the corresponding source article and provides both articles to the rectification engine, allowing factual inconsistencies to be identified and corrected more accurately.

Assumptions
Each AI-generated article has a corresponding source article associated with the same article_id.
Source articles are stored in the source_articles/ directory using the naming convention {article_id}.txt.
The source article is treated as the authoritative source of truth.
The rectification process should only correct factual errors and should not rewrite, summarize, or enrich the content.
Design Decisions
Added a dedicated get_source_article() function to separate source retrieval logic from business logic.
Extended the run() function interface to accept both AI-generated content and source content.
Updated the prompt to provide the source article as reference context for factual validation.
Kept changes minimal and localized to avoid impacting existing system behavior.
Challenges
Ensuring accurate mapping between AI-generated articles and their corresponding source articles.
Preventing the model from rewriting content instead of performing factual corrections.
Maintaining the original article structure and formatting after rectification.
Handling potential edge cases such as missing source files or invalid article identifiers.
Managing increased prompt size due to the inclusion of both source and generated content.
Outcome
By incorporating the source article into the rectification workflow, the system can validate generated content against the original information source, leading to improved factual accuracy and reduced risk of hallucinated corrections while preserving the original article structure.
