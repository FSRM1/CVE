foxcms<=1.2.5 sql injection vulnerability exists in batchCope method under app/admin/controller/Download.php in background 

![image-20250602160639650](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506021606919.png)

$ids passed by $param ['ids '];

![image-20250531152708968](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202505311527131.png)

Follow up param method

![image-20250602215901612](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506022159856.png)

Post here for reference.

![image-20250602215942235](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506022159392.png)

If you close it here, it will show that the operation is successful.

![image-20250602220050932](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506022200007.png)

Use sqlmap to run

![image-20250602220203114](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506022202281.png)

sql1.txt reads:

![image-20250602220234290](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202506022202361.png)
