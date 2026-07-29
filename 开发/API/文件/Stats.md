# [#](#Stats) Stats

> 相关文档: [文件系统](../../framework/ability/file-system.html)

描述文件状态的对象

## [#](#属性) 属性

### [#](#number-mode) number mode

文件的类型和存取的权限，对应 POSIX stat.st\_mode

### [#](#number-size) number size

文件大小，单位：B，对应 POSIX stat.st\_size

### [#](#number-lastAccessedTime) number lastAccessedTime

文件最近一次被存取或被执行的时间，UNIX 时间戳，对应 POSIX stat.st\_atime

### [#](#number-lastModifiedTime) number lastModifiedTime

文件最后一次被修改的时间，UNIX 时间戳，对应 POSIX stat.st\_mtime

## [#](#方法) 方法

### [#](#boolean-Stats-isDirectory) [boolean Stats.isDirectory()](Stats.isDirectory.html)

判断当前文件是否一个目录

### [#](#boolean-Stats-isFile) [boolean Stats.isFile()](Stats.isFile.html)

判断当前文件是否一个普通文件

Incorrect translation.