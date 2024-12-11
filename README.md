# MGR-docker-compose-demo
使用docker-compose一键搭建mgr
参考 https://www.cnblogs.com/ll409546297/p/16919642.html
master执行：
  CHANGE MASTER TO MASTER_USER='root', MASTER_PASSWORD='password' FOR CHANNEL 'group_replication_recovery';
  SET GLOBAL group_replication_bootstrap_group=ON;
  START GROUP_REPLICATION;
  SET GLOBAL group_replication_bootstrap_group=OFF;
  SELECT * FROM `performance_schema`.replication_group_members;

slave执行：
  CHANGE MASTER TO MASTER_USER='root', MASTER_PASSWORD='password' FOR CHANNEL 'group_replication_recovery';
  RESET MASTER;
  SET GLOBAL group_replication_recovery_get_public_key=ON;
  START GROUP_REPLICATION;
