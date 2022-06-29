---
hide:
  - navigation
  - toc
---

# Schéma de l'application web 

``` mermaid
flowchart TD
  home[Homepage]-->similarity[Document Similarity]--> 
  url[Enter URL CKAN for analyse similarity of document]-->|Function most_similar_url|cosine{{Cosine_analyser}} --> render([Render similarity document compare to other])
  SQL[(SQL Database)] -->|Count number of documents|home
  home[Homepage]-->topic[Topics Modelling visualizer] --> rangeslicertopics[Range slicer choose number of topics]-->|Function load_lda_model|lda{{LDA Topics model}} --> render_topics([Render visualisation Topics])
  api[(Call Api Datagrandest)]-->|Function Load dataset_similarity|rangeslicertopics
  home[Homepage]-->table[Table similarity]--> loadtable[/load table which compare similarity for all documents/] --> returntable([Render Table similarity])
  table --> buttontable[Click Button on page for access algothrim parameter page]--> algosimilar[/Algorithm for get all cosine similar for each document/] --> slicesimilarity[Range slicer : Choose the value of cosine similarity] -->|Function most_similar_all|render_similarity([return CSV])
  CSVselect[(CSV fiche_select.csv)] --> loadtable
  CSVsimilar[(CSV fiche_similar.csv)] --> loadtable
  render_similarity --> CSVselect
  render_similarity --> CSVsimilar

  style home fill:#3498db
  style table fill:#3498db
  style similarity fill:#3498db
  style topic fill:#3498db
  
  style SQL fill: #FF5733
  style api fill: #FF5733
  style CSVselect fill: #6D8B74
  style CSVsimilar fill: #6D8B74
  
  style url fill: #839AA8
  style rangeslicertopics fill: #839AA8
  style buttontable fill: #839AA8 
  style slicesimilarity fill: #839AA8         
```