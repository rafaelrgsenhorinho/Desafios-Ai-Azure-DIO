## Primeiro passo:
Vá no Azure AI Search resource, e selecione Import Data. No Data Source, selecione Azure Blob Storage, e complete as lacunas com essas informações:

Data Source: Azure Blob Storage
Data source name: coffee-customer-data
Data to extract: Content and metadata
Parsing mode: Default
Connection string: *Select Choose an existing connection. Select your storage account, select the coffee-reviews container, and then click Select.
Managed identity authentication: None
Container name: this setting is auto-populated after you choose an existing connection.
Blob folder: Leave this blank.
Description: Reviews for Fourth Coffee shops.

Depois aperte em Next: Add cognitive skills. No Attach Cognitive Services selecione o seu Azure AI Services. No Add enrichments, mude o nome para coffee-skillset, selecione Enable OCR and merge all text into merged_content field. Coloque o Source data field como merged_content, e o Enrichment granularity level para Pages (5000 character chunks). Depois selecione os itens: Extract location names, Extract key phrases, Detect sentiment, Generate tags from images, Generate captions from images.

No  Save enrichments to a knowledge store, selecione: Image projections, Documents, Pages, Key phrases, Entities, Image details, Image references. Se aparecer um aviso, selecione novamente o Select Choose an existing connection, e depois o coffeereviews. Selecione também o Azure blob projections: Document. E siga apertando o botão Next. No Name mude para coffee-index, o Key para metadata_storage_path. Abaixo selecione filterable para content, depois Next novamente.

Mude o nome para coffee-indexer, Schedule para Once. Expanda o Advanced Options e tenha certeza que o Base-64 Encode Keys esta selecionado. Depois aperte o botão Submit.

## Segundo passo:

Volte para a página da Azure AI Search,e no Menu lateral, na parte de Search Management, selecione Indexers. La você vai poder confirmar se ele foi criado com sucesso.Caso não tenha, espere uns minutinhos e aperte em Refresh. Selecionando o ndexer, você vai poder ver o status e comportamento dele.

## Terceiro passo:

Na pagina Inicial do Ai Search, no menu superior, selecione Search Explorer. Aqui você vai poder colocar os codigos em JSON para fazer pesquisa nos documentos que foram feitos upload no inicio do Desafio. Em view, selecione a opção JSON view, e depois você pode colocar os códigos para extrair as buscas. Exemplos:

{
    "search": "*",
    "count": true
}

----------------------------

{
 "search": "locations:'Chicago'",
 "count": true
}

----------------------------

{
 "search": "sentiment:'negative'",
 "count": true
}