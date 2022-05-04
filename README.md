# Azure Databricks Custom SAS Token
 How to use Azure SAS Token With Databricks
 
- Build the jar.
- Upload the jar to `dbfs`.
- Create the init script and copy uploaded jar to `/databricks/jars/`.
- Attached init script to the cluster and restart the cluster.
- Run the below commands in notebook to validate the SAS token:

`spark.conf.set("fs.azure.account.key.<account>.dfs.core.windows.net", dbutils.secrets.get("<access_key_name>", "<access_key_value>"))`

`spark.conf.set("fs.azure.account.auth.type.<account>.dfs.core.windows.net", "SAS")`

`spark.conf.set("fs.azure.sas.token.provider.type.<account>.dfs.core.windows.net", "com.databricks.support.sas.MockSASTokenProvider")`

`dbutils.fs.ls("abfss://<container_name>@<account_name>.dfs.core.windows.net/")`
