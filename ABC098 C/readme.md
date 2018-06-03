　最初に書いたのは一人ずつリーダーを決めて左右それぞれを走査、値を配列に足しておいて後で最小確認。これはTLE。
　なので、左から一つずつリーダーをずらしていき、本人、さっきまでのリーダーの人間の向きを確認することで、向きを変える人数をそれぞれ取得していく。
　計算量自体は確かにに減っているが、後半の問題でランタイムエラー発生。

### 配列に投げ込み続けるとスタックオーバーフローする
　どうやら配列がスタックオーバーフローしているようである（最大で3*10^5）。つまり、配列に取得した数字を投げ込んで後で最小値を取るという方法がそもそもNG。
　これは単純に「現在の値」「最小値」を定義しておいて、リーダーをずらす際に新しく取得した数値が最小値なら「最小値」を更新するだけで解決する。
　JSに限らない話な気はするが、「記録を更新していく」みたいな書き方を（競プロにおいては）嫌がってはいけないという教訓。