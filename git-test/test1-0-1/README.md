# git标签
 添加标签
```git tag -a v1.0.1```
 查看log日志(标签显示)
```git log --oneline --decorate --graph```
 追加标签
```git tag -a v0.9 85fc7e7```
 查看标签
```git tag```
 指定标签信息命令
```git tag -a 标签名 -m "标签信息"```
 PGP签名标签命令
```git tag -s 标签名 -m "标签信息"```