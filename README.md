# RDS to Knowledge Graph (RDS2KGS)

An automated rule-based pipeline that transforms relational database schemas into graph-structured JSON files, visualisation-ready outputs, and LLM prompts for dimensional modelling analysis.

## Pipeline Overview
```
schema.json -> graph JSON -> mapping specs -> yFiles visualisation -> LLM prompts
```

## What this does

1. **schema_to_graph.py** - Parses relational schema JSON files and converts tables and foreign key relationships into graph nodes and edges
2. **mapping_specs.py** - Transforms graph JSON into structured mapping specifications with PK/FK integrity handling
3. **mapping_to_yFiles.py** - Converts mapping specs into yFiles-compatible graph JSON for visualisation
4. **llm_prompts.py** - Generates structured natural language prompts from mapping specs for LLM-based dimensional modelling analysis

## Sample Output

See [examples/graph_schemas/academic_graph.json](examples/graph_schemas/academic_graph.json) for a sample graph output generated from the Spider academic database.

The output captures:
- 15 table nodes with columns and primary keys
- 18 foreign key edges representing entity relationships
- Ready for import into Neo4j or yFiles visualisation

Validation reports for each database are available in examples/spider/<db_id>/validation.log - confirming zero structural issues across all processed schemas.

## Scale

Pipeline successfully processed 100 databases from the Spider benchmark, generating graph outputs across domains including academic, airline, hospital, and financial schemas.

## Tech Stack

- Python 3.x
- JSON schema transformation
- yFiles graph visualisation format
- OpenAI LLM integration
- Spider dataset (Yale cross-domain SQL benchmark)

## Dataset

Built and tested on the [Spider dataset](https://yale-lily.github.io/spider) - a large-scale cross-domain text-to-SQL benchmark developed by Yale University containing 200+ databases across 138 domains.

To run the pipeline, download Spider and place the database folders inside examples/spider/.

## How to Run

Run scripts in this order:

python src/schema_to_graph.py
python src/mapping_specs.py
python src/mapping_to_yFiles.py
python src/llm_prompts.py

## Project Background

Capstone project exploring automated knowledge graph construction from structured relational datasets using rule-based transformation and LLM assistance.

## Author

Ashwin Vidyadhar Shirashyad - pipeline architecture, schema extraction, graph transformation, mapping specification, yFiles visualisation output, and LLM prompt generation.
