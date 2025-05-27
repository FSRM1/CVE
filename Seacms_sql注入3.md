Seacms V13.3 has an SQL injection vulnerability that allows an authenticated attacker to exploit the database to steal information or compromise the database

Download address：https://www.seacms.com/download/

![image-20250528004403051](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202505280044387.png)

This vulnerability exists in line 242 of admin_collect.php, id value is  controllable by post parameter, and there is no check on sql statement,  resulting in sql injection vulnerability.

![image-20250528004606596](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202505280046735.png)

![image-20250528004639837](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202505280046926.png)

![image-20250528004717538](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202505280047707.png)