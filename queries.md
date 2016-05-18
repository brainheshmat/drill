# HDFS
select count(*) from hdfs.`/data/raw_data/pcmd/lte/mme1/150707/*.geo` where columns[2] > 35.00;

# Local file system
select count(*) from dfs.`/home/ubuntu/mme1/*.geo` where columns[2] > 35.00;
