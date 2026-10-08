# Informacja o naruszeniu ochrony danych osobowych — strona dla pacjentów

Statyczna strona internetowa Gabinetu stomatologicznego Mariola Krajewska z informacją dla
pacjentów o naruszeniu ochrony danych osobowych, do którego doszło u dostawcy oprogramowania
gabinetowego. Strona realizuje obowiązek zawiadomienia osób, których dane dotyczą (art. 34 RODO).

Adres strony: **https://gabinetkrajewska.github.io/**

Pacjenci otrzymują SMS z adresem strony podanym jako tekst do ręcznego przepisania — dlatego adres
strony nie powinien się zmieniać.

## ⚠️ To repozytorium jest publiczne

Każdy w internecie widzi wszystkie pliki i całą historię zmian.

- **Nie wolno** umieszczać tu żadnych danych pacjentów: list pacjentów, numerów PESEL, numerów
  telefonów, adresów, dokumentacji medycznej, eksportów z systemu gabinetowego.
- **Nie wolno** wgrywać dokumentów źródłowych (pliki `.docx`, `.pdf`, `.xlsx`, `.csv`) — plik
  `.gitignore` blokuje je zawczasu, ale ostatecznie odpowiada za to osoba wgrywająca zmiany.
- Usunięcie pliku późniejszym commitem **nie usuwa go z historii** — jeśli coś takiego trafi do
  repozytorium, trzeba je usunąć w całości i założyć nowe.

## Zawartość

| Plik | Do czego służy |
| --- | --- |
| `index.html` | Cała treść strony |
| `style.css` | Wygląd strony (jeden arkusz, bez zewnętrznych zasobów) |
| `favicon.svg` | Mała ikona strony widoczna na karcie przeglądarki |
| `robots.txt` | Blokuje indeksowanie strony przez wyszukiwarki |
| `.nojekyll` | Wyłącza przetwarzanie plików przez GitHub Pages |
| `.gitignore` | Lista plików, które nigdy nie mają trafić do repozytorium |

Strona nie używa JavaScriptu, plików cookies, analityki, formularzy ani żadnych zasobów z innych
serwerów. Jedyne odnośniki wychodzące prowadzą do `gov.pl` i `mobywatel.gov.pl` oraz do telefonu
(`tel:`) i poczty (`mailto:`).

## Do uzupełnienia przed publikacją

W pliku `index.html`, w sekcji **Kontakt**, znajdują się dwa znaczniki do wypełnienia. Każdy
występuje w jednym wierszu **dwa razy**: raz w adresie odnośnika, raz w widocznym tekście.

```html
<p>Telefon: <a href="tel:[TELEFON]">[TELEFON]</a> <span class="do-uzupelnienia">— do uzupełnienia</span><br>
  E-mail: <a href="mailto:[E-MAIL]">[E-MAIL]</a> <span class="do-uzupelnienia">— do uzupełnienia</span><br>
```

Po uzupełnieniu powinno to wyglądać na przykład tak. Numer telefonu w odnośniku `tel:` zapisujemy
bez spacji, z numerem kierunkowym kraju, a w widocznym tekście zamiast spacji wstawiamy `&nbsp;`,
żeby numer nie łamał się na dwa wiersze. Całe fragmenty `<span>— do uzupełnienia</span>` usuwamy:

```html
<p>Telefon: <a href="tel:+48890000000">89&nbsp;000&nbsp;00&nbsp;00</a><br>
  E-mail: <a href="mailto:gabinet@przyklad.pl">gabinet@przyklad.pl</a><br>
```

Znaczniki łatwo odnaleźć, szukając w pliku tekstu `uzupeł`. Nad każdym z nich jest komentarz
`<!-- UZUPEŁNIĆ: ... -->`, który **po wypełnieniu należy usunąć**.

## Jak zaktualizować treść strony

1. Otwórz `index.html` w zwykłym edytorze tekstu (nie w Wordzie) albo bezpośrednio na GitHubie
   (przycisk z ołówkiem nad plikiem).
2. Zmień tylko tekst między znacznikami, np. między `<p>` a `</p>`. Nie zmieniaj samych znaczników.
3. **Zawsze dopisz datę aktualizacji.** Na dole pliku, w stopce, jest wiersz:

   ```html
   <p>Data publikacji: 8 października 2026. Ostatnia aktualizacja: 8 października 2026.</p>
   ```

   Datę publikacji zostaw bez zmian, a datę po słowach „Ostatnia aktualizacja" zmień na dzisiejszą.
   Dzięki temu pacjent widzi, że informacja jest aktualna.
4. Zapisz zmiany (na GitHubie: „Commit changes"). Strona odświeża się zwykle w ciągu minuty.
   Jeżeli nie widać zmian, odśwież stronę w przeglądarce z wciśniętym klawiszem Shift.

Zmiany z komputera, przez wiersz poleceń:

```bash
git add -A
git commit -m "Aktualizacja treści informacji"
git push
```

## Czego nie zmieniać bez potrzeby

- Treści w sekcji „Pełna treść informacji o naruszeniu ochrony danych osobowych" — jest to
  formalny komunikat uzgodniony co do słowa.
- Adresów `gov.pl` i `mobywatel.gov.pl`.
- Znaczników `<meta>` w górnej części pliku (odpowiadają m.in. za to, że strona nie jest
  indeksowana przez wyszukiwarki i nie wysyła żadnych danych na zewnątrz).

## Treść SMS-a wysyłanego pacjentom

Adres strony podajemy jako tekst do ręcznego przepisania — bez „https://" i bez odnośnika, żeby
wiadomość nie przypominała prób oszustwa i żeby pacjenci przyzwyczajali się nie klikać w linki
z SMS-ów. SMS nie zawiera polskich znaków (zmieściłby się wtedy tylko 70 znaków zamiast 160).

```
Gabinet stomatologiczny Mariola Krajewska: wazna informacja. Wpisz w przegladarce: gabinetkrajewska.github.io Tel. 000 000 000. Nie prosimy o dane ani oplaty.
```

W miejsce `000 000 000` wpisujemy numer gabinetu. Na numer telefonu zostało **13 znaków** — mieści
się np. `89 755 00 00`. Cała wiadomość musi mieć **najwyżej 160 znaków**, inaczej operator podzieli
ją na dwie wiadomości.

## Publikacja na GitHub Pages

Repozytorium musi nazywać się dokładnie `gabinetkrajewska.github.io` i być publiczne. W ustawieniach
repozytorium: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / katalog `/ (root)`**,
a następnie zaznaczamy **Enforce HTTPS**. Pierwsza publikacja trwa zwykle 1–2 minuty.

Jeśli adres repozytorium kiedykolwiek się zmieni, trzeba poprawić adres w trzech miejscach:
w `index.html` (znacznik `og:url`), w tym pliku oraz w treści SMS-a.

## Podgląd lokalny

W katalogu z plikami:

```bash
python3 -m http.server 8000
```

Następnie w przeglądarce: `http://localhost:8000`.
