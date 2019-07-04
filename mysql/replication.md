<!-- TITLE: Replication -->
<!-- SUBTITLE: A quick summary of Replication -->

# take snapshot for slave.
mysqldump -umyuser -pmypassword --all-databases --flush-logs --master-data=1 | gzip > all.masterNode_20190212.dmp.gz

Commando