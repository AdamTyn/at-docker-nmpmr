### AT-Docker/nmpmr

1. *master* 分支为 `php7.2` 版本
2. [2020-4-24] 所有分支均添加了 `xdebug` 扩展（如果使用 `swoole` 出现冲突，可以在 */usr/etc/php/conf.d* 目录下 **重命名 *docker-ext-xdebug.ini* 文件** 即可禁用此扩展）
3. [2020-4-25] 新增 `php7.4` 版本，切换分支到 *php74* ，重新编译容器即可

