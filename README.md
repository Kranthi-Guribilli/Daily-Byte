# Elasticsearch Low-Level Java Client
* Elastic has recently released a new Java client for Elasticsearch, which is more lightweight than the previous High Level Rest client while providing a more complete API coverage and an easier to use DSL-like eperience.
* The Java client for Elasticsearch provides strongly typed requests and responses for all Elasticsearch APIs.
* It delegates protocol handling to an http client such as the **Elasticsearch low level REST client** that takes care of all transport-level concerns (http conncetion establishment and pooling, retries, etc).

  ## Creating a Client:
    - Batteries included, some assembly required
      ```
      RestClient httpClient = RestClient
        .builder(new HttpHost("localhost", 8081)) <--- Http & cluster node discovery layer
        .build();
      ```
      ```
      JacksonJsonMapper jsonMapper = new JaksonJsonMapper(); <--- Json parser & object mapper
      ```
      ```
      ElasticsearchTransport transport = new RestClientTransport(httpClient, jsonMapper); <--- Transport: groups json and http
      ```
      ```
      Elasticsearch client = new ElasticsearchClient(transport); <--- ES API client
      ```
      ```
      ElasticsearchAsyncClient asyncClient = new ElasticsearchAsyncClient(transport); <--- Also available in async form
      ```
  * **An example Kibana's template**
  ```
  PUT /products/_doc/abc
  {
  "id": "abc",
  "name": "Bag",
  "prics": 24.0
  }
  ```
  * **Classic builder style**
  ```   
      Product product = new Product("abc", "Apple", 24.0);
      IndexRequest<Product> indexRequest = new IndexRequest.Builder<>()
         .index("products")
         . id("abc")
         .document(product)
         .build();
      client.index(indexRequest);
  ```
  * **Functional builder style**
  ```
  Product product = new Product("abc", "Apple", 24.0);
  client.index(builder -> builder
    .index("product")
    .id(product.id())
    .documetn(product)   <----- mapping from application objects to JSON
  );
  ```

  ## Searching
  * **Classic builder style**
  ```
  TermQuery query = QueryBuilders.term(()
      .field("name")
      .value("bag")
      .build();
  SearchRequest request = new SearchRequest.Builder()
      .index("products")
      .query(query) <--- query is a union of all query types to allow completion-driven discovery
      .build();
  SearchResponse<Product> search =
      client.search(
        request,
        Product.class
      );
  Product product = search.hits().hits().get(0).source(); <----- mapping from JSON to application objects
  ```
  * **Splitting complex DSL**
    ```
    TermQuery termQuery = TermQuery.of(t -> t
        .field("name")
        .value("bag")
      );
    SearcResponse<Product> search =
      client.search(b -> b
        .index("products")
        .query(termQuery),
        Product.class
    );
    Product product = search.hits().hits().get(0).source();

## Aggregations
* **Creating the aggregation**
  ```
  SearchREsponse<Void> search = client
    .search(b -> b
        .index("products")
        .size(0)
        .aggregations("price-histo", a->a
            .histogram(h->h
                .field("price")
                .interval(20.0)
            )
          ),
          Void.class  <---- no docs in the response
  );
  ```
  * **Navigating aggregation results**
    ```
    {
      "took" : 2,
      '''
      "aggregations" : {
        "histogram#price-histo" : {
            "buckets" : [
                {
                  "key" : 0.0,
                  "doc_count" : 1000
                 },
                 {
                    "key" : 50.0,
                    "doc_count" : 281
                  }
              ]
          }
      }
    }
    ```
    ```
    SearchResponse<Product> search = client.search(...);
    long firstBucketCount = search.aggregations()
        .get("price-histo")     <--- get a named aggregation
        .histogram()
        .buckets().array()
        .get(0)
        .docCount();
    ```
    
  
