+++
author = "@yu-kgr"
categories = ["TIL"]
date = "2018-08-03"
description = "2018/08 - one week I Learned | 一週間で知った事・学んだ事の個人的な備忘録"
featured = "/img/til/til.jpg"
featuredalt = "til"
featuredpath = "https://kglabo.com"
title = "2018/08 - one week I Learned"
type = "post"
draft = "true"
+++

# 今週、知った/学んだこと

<!-- tags = [""] -->

## 2018/07/30- Learned

7月30日（月）のToday I Leaned.

### ES2015について

#### ESLint

- Unexpected block statement surrounding arrow body (arrow-body-style)
- 関数がreturn分しか含まない場合は、ブレース（`{}`）とretun文とセミコロンを省略できる。

```JavaScript
() => {
  return 1;
}

// 省略したケース
() => 1
```

