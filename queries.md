# HDFS
select count(*) from hdfs.`/data/raw_data/pcmd/lte/mme1/150707/*.geo` where columns[2] > 35.00;

# Local file system
select count(*) from dfs.`/home/ubuntu/mme1/*.geo` where columns[2] > 35.00;


curl -X POST -H "Content-Type: application/json" -d '{"queryType":"SQL", "query": "SELECT columns[145],columns[146] from dfs.tmp.///dodata_tmp/*.csv` where columns[145] between '42.2331' and '42.2332' and columns[146] between '-71.79' and '-71.7888'"}' http://localhost:8047/query.json

curl -X POST -H "Content-Type: application/json" -d '{
  "name" : "dfs",
  "config" : {
    "type" : "file",
    "enabled" : true,
    "connection" : "file:///",
    "config" : null,
    "workspaces" : {
      "root" : {
        "location" : "/",
        "writable" : false,
        "defaultInputFormat" : null
      },
      "tmp" : {
        "location" : "/tmp",
        "writable" : true,
        "defaultInputFormat" : null
      }
    },
    "formats" : {
      "psv" : {
        "type" : "text",
        "extensions" : [ "tbl" ],
        "delimiter" : "|"
      },
      "csv" : {
        "type" : "text",
        "extensions" : [ "csv" ],
        "delimiter" : ",",
        "skipFirstLine": true
      },
      "tsv" : {
        "type" : "text",
        "extensions" : [ "tsv" ],
        "delimiter" : "\t"
      },
      "parquet" : {
        "type" : "parquet"
      },
      "json" : {
        "type" : "json",
        "extensions" : [ "json" ]
      },
      "avro" : {
        "type" : "avro"
      },
      "sequencefile" : {
        "type" : "sequencefile",
        "extensions" : [ "seq" ]
      },
      "csvh" : {
        "type" : "text",
        "extensions" : [ "csvh" ],
        "extractHeader" : true,
        "delimiter" : ","
      }
    }
  }
}' http://localhost:8047/storage/dfs.json
