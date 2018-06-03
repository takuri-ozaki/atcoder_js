　問題自体は実は偶奇判定するだけの問題で（愚直にループ書くと当然TLE）だが、JSで解いたときにハマりポイントが２点あり。　問題自体は実は偶奇判定するだけの問題で（愚直にループ書くと当然TLE）だが、JSで解いたときにハマりポイントが２点あり。

### JSは大きい数字が扱えない
　JSでの整数の精度保証は2<sup>53</sup> - 1までであり、これは10<sup>16</sup>に少し届かない程度である。つまり、これ以上の数字は「大体」でしか合っていない。偶基判定は末尾一桁なのでこのまま扱うと死にます。
　逆に言えば、偶基判定は末尾一桁さえ取得できれば良いので、計算する前に操作回数Kから末尾一桁以外削ってしまえば良い。
（参考）https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Number/isSafeInteger

### 謎の空白？でハマる
　上記工夫を入れても何故か通らないケースが数個あった。終了後、他にJSで解いている方がいたので読んでみると、標準入力を読む部分に.trim()を入れていた。
　実際に入れてみると何の問題もなく通ってしまう。与えられたケースに謎空白が入っていて、挙動がおかしくなっていたようだ。
　AtCoderの標準入力例をそのまま流用すると以上のような問題が起きてしまう。多分他の問題でも同じようなことが起きるリスクがあるので、今はとりあえず末尾に.trim()を入れるようにしている。