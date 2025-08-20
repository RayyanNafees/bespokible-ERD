# Bespokible-related ER Diagrams

This the repository of all the bespokible project related SQL dump files & their ER
diagrams and other related information documents

The following projects have been take into the account of research:

## Tools available:
- **[SQLFlow](https://sqlflow.gudusoft.com/)** - Just paste the db dump, choose the DBMS and generate an ordinary ER diagram
- **[Eraser.io](httpsL://eraser.io)** - Paste the db dump and generates a Color Coded diagram with AI or their [design language](https://docs.eraser.io/docs/syntax-1)
- **[NotebookLM Eraser Diagram Workspace](https://notebooklm.google.com/notebook/5148d9de-4e16-4a26-b7a5-964208f10a79)** - AI diagram generators have short Contexts and might not generate accurate diagrams like SQLFlow or Graphviz does, NotebookLM is used to generate the Graphviz/Eraser Diagram code from the SQL over long contexts using AI

### Other Tools:
Never tried these out but were recommended by the search engine, much like [SQLFlow](https://sqlflow.gudusoft.com/), can be used to accurately generate ERDs
#### Web Based
- **[FowHigh](https://flowhigh.io/sql-visualizer)**
- **[DrawDB](https://drawdb.vercel.app/editor)** - Free Service for SQL visualization, share, schema editor, and more (check the [screenshot](/chartdb.png))


#### Native Applications
- **[pgModeler](https://github.com/nkb84/pgmodeler-windows)** - A PostgreSQL Database Modeler, can be used to generate ERDs from SQL dumps
- **[DBDesigner 4](https://www.dbdesigner.net/)** - A visual database design system that integrates database design, modeling, creation and maintenance into a single, seamless environment
- **[HTML dbdesigner](https://github.com/akreienbring/dbdesigner)** - An express.js project to generate ERDs from SQL dumps

## Generated ER Diagrams
The following diagrams have been generated using [Eraser.io AI diagram Generater](https://www.eraser.io/ai/erd-generator)
Shows the Docs site, PNG & SVG images of ERD and the SQL dump they were made from (can be used to visualize using [SQLFlow](https://sqlflow.gudusoft.com/)

> [!IMPORTANT]
> The Medusa Dump file contained thousands of lines of SQL code even after truncating the inserts, since AI have limited contexts, they were generated via using the two following approches
> - Medusa A - The thousands of lines of SQL code was just pasted to generate the AI ERD which seemed to lack all the tables
> - Medusa B - Was provided into the [NotebookLM ERD Wokspace](https://notebooklm.google.com/notebook/5148d9de-4e16-4a26-b7a5-964208f10a79) to generate the [eraser diagramming code](https://docs.eraser.io/docs/syntax-1) which was then used in the [eraser platform](https://app.eraser.io) to more accurately generate all the table relations
> > For accurate Medusa ERD , using the [SQLFlow](https://sqlflow.gudusoft.com/) tool via [Medusa Dump file](/medusa/medusa-dump.sql) is recommended

project | site | ERD.png | ERD.svg | SQL dump
-- | -- | -- | -- | --
Medusa A| [Medusajs.com](https://medusajs.com/)| [medusa-a.png](/medusa/medusa-a.png)  | [medusa-a.svg](/medusa/medusa-a.svg) | [medusa-dump.sql](/medusa/medusa-dump.sql)
Medusa B| [Medusa Docs](https://docs.medusajs.com/)| [medusa-b.png](/medusa/medusa-b.png)  | [medusa-b.svg](/medusa/medusa-b.svg)| [medusa-dump.sql](/medusa/medusa-dump.sql)
Vendure | [Venture Docs](https://docs.vendure.io/) | [vendure.png](/vendure/vendure.png) | [vendure.svg](/vendure/vendure.svg)| [vendure-dump.sql](/vendure/vendure-dump.sql)
Bespokible | [Bespokible Vercel](https://bespokible.vercel.app) | [bespokible.png](/bespokible/bespokible.png) | [bespokible.svg](/bespokible/bespokible.svg) | [bespokible-dump.sql](/bespokible/bespokible-dump.sql)

> Also have a look at [Vendure Tables Document](/vendure/vendure-tables.md)

## Other Project Recommendations
- **[Saleor](https://saleor.io/)** - Has a [GraphQL Inspector](https://docs.saleor.io/api-usage/developer-tools) that can reveal the full shcema of the API, ERD is only possible after docker setup and manual dbms dump
- **[InvenTree](https://inventree.org/)** -