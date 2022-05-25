## Bir Commit Mesajının Anatomisi

İyi bir commit mesajı 3 amaca hizmet eder.
* Review sürecini hızlandırır.
* İyi bir realese notu yazmamıza yardımcı olur.
* Gelecek zamanda kodda nerede değişiklik yapıldığını ve neden bu değişikliğe gidildiğini vb. durumları anlamamıza yardımcı olur.



Temel Commit Mesajı

```
git commit -m <mesaj>
```
Detaylı Commit Mesajı
```
git commit -m <baslik> -m <aciklama>
```

İyi Bir Commit Mesajı Nasıl Yazılır ?

* Büyük harf ve noktalama: Commit mesajı büyük harfle başlamalı ve nokta ile bitmemeli. Conventional commit mesajları tümüyle küçük harflerle yazılmalıdır.
  > Conventional Commmit: Projede major bir değişiklik olacağında kullanılır.
* Commit mesajı yazarken emir kipini ve şimdiki zamanı kullanın.
> Örnek: 'Add fix for dark mode toggle state'
* Commit Türü: Commit mesajı yazarken ilk kelimeler "Added" ,"Fixed" gibi yanlış kullanımlar yerine "Add","Fix","Edit" gibi başlamalıdır.

