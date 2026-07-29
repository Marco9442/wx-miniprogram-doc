# [#](#FileSystemManager) FileSystemManager

> 相关文档: [文件系统](../../framework/ability/file-system.html)

文件管理器，可通过 [wx.getFileSystemManager](wx.getFileSystemManager.html) 获取。

## [#](#方法) 方法

### [#](#FileSystemManager-access-Object-object) [FileSystemManager.access(Object object)](FileSystemManager.access.html)

判断文件/目录是否存在

### [#](#FileSystemManager-appendFile-Object-object) [FileSystemManager.appendFile(Object object)](FileSystemManager.appendFile.html)

在文件结尾追加内容

### [#](#FileSystemManager-saveFile-Object-object) [FileSystemManager.saveFile(Object object)](FileSystemManager.saveFile.html)

保存临时文件到本地。此接口会移动临时文件，因此调用成功后，tempFilePath 将不可用。

### [#](#FileSystemManager-getSavedFileList-Object-object) [FileSystemManager.getSavedFileList(Object object)](FileSystemManager.getSavedFileList.html)

获取该小程序下已保存的本地缓存文件列表

### [#](#FileSystemManager-removeSavedFile-Object-object) [FileSystemManager.removeSavedFile(Object object)](FileSystemManager.removeSavedFile.html)

删除该小程序下已保存的本地缓存文件

### [#](#FileSystemManager-close-Object-object) [FileSystemManager.close(Object object)](FileSystemManager.close.html)

关闭文件

### [#](#undefined-FileSystemManager-closeSync-Object-object) [undefined FileSystemManager.closeSync(Object object)](FileSystemManager.closeSync.html)

同步关闭文件

### [#](#FileSystemManager-copyFile-Object-object) [FileSystemManager.copyFile(Object object)](FileSystemManager.copyFile.html)

复制文件

### [#](#FileSystemManager-fstat-Object-object) [FileSystemManager.fstat(Object object)](FileSystemManager.fstat.html)

获取文件的状态信息

### [#](#Stats-FileSystemManager-fstatSync-Object-object) [Stats FileSystemManager.fstatSync(Object object)](FileSystemManager.fstatSync.html)

同步获取文件的状态信息

### [#](#FileSystemManager-ftruncate-Object-object) [FileSystemManager.ftruncate(Object object)](FileSystemManager.ftruncate.html)

对文件内容进行截断操作

### [#](#undefined-FileSystemManager-ftruncateSync-Object-object) [undefined FileSystemManager.ftruncateSync(Object object)](FileSystemManager.ftruncateSync.html)

对文件内容进行截断操作

### [#](#FileSystemManager-getFileInfo-Object-object) [FileSystemManager.getFileInfo(Object object)](FileSystemManager.getFileInfo.html)

获取该小程序下的 本地临时文件 或 本地缓存文件 信息

### [#](#FileSystemManager-mkdir-Object-object) [FileSystemManager.mkdir(Object object)](FileSystemManager.mkdir.html)

创建目录

### [#](#FileSystemManager-open-Object-object) [FileSystemManager.open(Object object)](FileSystemManager.open.html)

打开文件，返回文件描述符

### [#](#string-FileSystemManager-openSync-Object-object) [string FileSystemManager.openSync(Object object)](FileSystemManager.openSync.html)

同步打开文件，返回文件描述符

### [#](#FileSystemManager-read-Object-object) [FileSystemManager.read(Object object)](FileSystemManager.read.html)

读文件

### [#](#ReadResult-FileSystemManager-readSync-Object-object) [ReadResult FileSystemManager.readSync(Object object)](FileSystemManager.readSync.html)

读文件

### [#](#FileSystemManager-readCompressedFile-Object-object) [FileSystemManager.readCompressedFile(Object object)](FileSystemManager.readCompressedFile.html)

读取指定压缩类型的本地文件内容

### [#](#ArrayBuffer-FileSystemManager-readCompressedFileSync-Object-object) [ArrayBuffer FileSystemManager.readCompressedFileSync(Object object)](FileSystemManager.readCompressedFileSync.html)

同步读取指定压缩类型的本地文件内容

### [#](#FileSystemManager-readFile-Object-object) [FileSystemManager.readFile(Object object)](FileSystemManager.readFile.html)

读取本地文件内容。单个文件大小上限为100M。

### [#](#FileSystemManager-readZipEntry-Object-object) [FileSystemManager.readZipEntry(Object object)](FileSystemManager.readZipEntry.html)

读取压缩包内的文件

### [#](#FileSystemManager-readdir-Object-object) [FileSystemManager.readdir(Object object)](FileSystemManager.readdir.html)

读取目录内文件列表

### [#](#FileSystemManager-rename-Object-object) [FileSystemManager.rename(Object object)](FileSystemManager.rename.html)

重命名文件。可以把文件从 oldPath 移动到 newPath

### [#](#FileSystemManager-rmdir-Object-object) [FileSystemManager.rmdir(Object object)](FileSystemManager.rmdir.html)

删除目录

### [#](#FileSystemManager-stat-Object-object) [FileSystemManager.stat(Object object)](FileSystemManager.stat.html)

获取文件 Stats 对象

### [#](#FileSystemManager-truncate-Object-object) [FileSystemManager.truncate(Object object)](FileSystemManager.truncate.html)

对文件内容进行截断操作

### [#](#undefined-FileSystemManager-truncateSync-Object-object) [undefined FileSystemManager.truncateSync(Object object)](FileSystemManager.truncateSync.html)

对文件内容进行截断操作 (truncate 的同步版本)

### [#](#FileSystemManager-unlink-Object-object) [FileSystemManager.unlink(Object object)](FileSystemManager.unlink.html)

删除文件

### [#](#FileSystemManager-unzip-Object-object) [FileSystemManager.unzip(Object object)](FileSystemManager.unzip.html)

解压文件

### [#](#FileSystemManager-write-Object-object) [FileSystemManager.write(Object object)](FileSystemManager.write.html)

写入文件

### [#](#WriteResult-FileSystemManager-writeSync-Object-object) [WriteResult FileSystemManager.writeSync(Object object)](FileSystemManager.writeSync.html)

同步写入文件

### [#](#FileSystemManager-writeFile-Object-object) [FileSystemManager.writeFile(Object object)](FileSystemManager.writeFile.html)

写文件

Incorrect translation.