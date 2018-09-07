+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-09-06"
description = "Hugoで構築していたGithubPages&CircleCI1.0で運用していたブログをNetlifyに移行したお話です。"
featured = "/img/2018/09/netlify-head.png"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "CircleCIの1.0->2.0移行がめんどくさかったので、Netlifyに移行したら糞便利だった話"
type = "post"
draft = "false"
+++

# CircleCIからNetlifyに移行した記録

そういえば、社内の方がパワープッシュしたり、[kanazawa.rb#72](https://kzrb.org/meetup/72/report.html)に参加した時にステッカーをもらったNetlify。  
なんか良さげなものだと聞いてたいたものの、ほー、ふーん。で終わっておりました。

今回、ちょうどCircleCi@1.0から2.0への移行が諸事情でめんどくさすぎたので、思い切ってNetlifyに変えてみた記録。

- 結果として楽すぎてビックリした。
- 内容はうっっっっっっっすい

## 10分もかからぬ、この簡単さ。

Gitが格納されているサーバを各社の中から選択する
![Create a new site](/blog/using-netlify/01.png)

「New site from git」を選択
![New site from git](/blog/using-netlify/02.png)

該当のリポジトリを選択する
![Continuous Deployment: GitHub](/blog/using-netlify/03.png)

Netlify側で勝手にHugo側の設定をよしなにしてくれるので確認
![Deploy settings for yu-kgr/kglabo](/blog/using-netlify/04.png)

「Deploy Site」を押すとGeneratを開始
![Site Deploy in Progress](/blog/using-netlify/05.png)

1-2分待つと完了
![done](/blog/using-netlify/06.png)

もうできた…恐ろしい子…！！！
![done](/blog/using-netlify/07.png)

この後、独自ドメインのAとかCNAMEとかネームサーバをよしなにするだけでした。しゅごい。

### 感想

- あまりにも簡単に出来すぎて「ん？」ってなりました。
- 5分後ぐらいに物事を理解した後「circle.yml」をゴミ箱に放り投ました。
- ここまで全部、無料です。http/2やCiも使えるんだぜ・・・もう意味わからん。

