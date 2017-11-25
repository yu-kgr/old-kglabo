+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2017-05-08"
description = "リポジトリにssh接続でgit cloneする為にssh-keygen -f hogehogeで、別名pubファイルを作ったら永遠にcloneできなかったので、なんとかした。"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
linktitle = ""
title = "リポジトリにssh接続でgit cloneする為にssh-keygen -f hogehogeで、別名pubファイルを作ったら永遠にcloneできなかった話"
type = "post"
+++

## 発生した問題

githubの既存リポジトリから、sshでgit cloneしたかったので、  
[お前らのSSH Keysの作り方は間違っている](http://qiita.com/suthio/items/2760e4cff0e185fe2db9)を参考にして暗号強度を高めつつ、  
`ssh-keygen -f github_id_rsa` で別名のpubファイルを作成してcloneした所、  
下記のようなエラーが発生した。  

```
Warning: Permanently added the RSA host key for IP address '***.***.***.**' to the list of known hosts.
Permission denied (publickey).
```

## 対処方法

GitHub へのアクセス時に、 `~/.ssh/id_rsa` や `~/.ssh/id_dsa` ではなく、  
別名で認証鍵を作成した場合は、 `~/.ssh/config` ファイルを作成して、  
下記設定を記述する必要がある。

また、configファイルに関しては、Permissionを600にする必要がある。


```
# ~/.ssh/config

Host github.com
    IdentityFile ~/.ssh/github_id_rsa
```

上記の設定を加える事で、無事問題なくcloneする事ができた。
