# Web4  XSS Me
原本看到題目超級興奮，是常找的XSS
結果 😧
> 我到現在還沒寫出來，等Writeup
## 限制
* payload只能54個字元
* Cookie設定了HttpOnly => document.cookie拿不到內容
* CSP策略：default-src: 'self' ...忘了 => 不能載入外部src
* 在<script>裏面，所以要閉合
  
然後我就不會了
