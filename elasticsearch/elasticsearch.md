# ElasticSearch
[Home](../README.md)

Here are the explanations for the concepts related to Elasticsearch and the updated commands:

- *Nodes*: Nodes are individual servers within an Elasticsearch cluster. The default cluster name is "elasticsearch".

- *Indices*: Indices are like collections or databases in Elasticsearch. They store and organize data in a structured manner. You can think of them as similar to "tables" in a traditional database.

- *Documents*: Documents are the individual units of data stored within an index. They are JSON objects that contain the actual data.

- *Types*: Types are used to categorize documents within an index. They define the schema or structure of the documents. However, starting from Elasticsearch 7.x, types are deprecated and considered optional.

Now, let's look at the updated commands:

1. Run Elasticsearch Docker image:
   ```bash
   docker run -p 9200:9200 -p 9300:9300 --name elasticsearch -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.11.3
   # This command runs the Elasticsearch Docker image, exposes ports 9200 and 9300 for HTTP and transport communication, sets the cluster discovery type to "single-node" for a single-node cluster configuration, and uses the Elasticsearch 7.11.3 version.
   ```

2. Run Kibana on local Docker image:
   ```bash
   docker run --link <container-id>:<container-name> -p 5601:5601 <kibana-container-id>
   # Replace <container-id> with the ID of the Elasticsearch container you want to link to, <container-name> with the desired name for the linked container, and <kibana-container-id> with the ID or name of the Kibana container image you want to run.
   ```

Please note that the `<container-id>`, `<container-name>`, and `<kibana-container-id>` should be replaced with the actual container IDs or names according to your setup.