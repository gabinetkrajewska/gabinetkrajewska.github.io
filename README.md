# Informacja o naruszeniu ochrony danych osobowych — strona dla pacjentów

Statyczna strona internetowa Indywidualnej Praktyki Stomatologicznej Mariola Krajewska
z informacją dla pacjentów o naruszeniu ochrony danych osobowych, do którego doszło u dostawcy
oprogramowania gabinetowego — firmy FELG Software sp. z o.o. (program FELG Dent). Strona realizuje
obowiązek zawiadomienia osób, których dane dotyczą (art. 34 RODO).

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

## Dane kontaktowe na stronie

W sekcji **Kontakt** podany jest wyłącznie telefon i adres gabinetu — gabinet nie podaje na tej
stronie własnego adresu e-mail. Obok znajduje się adres e-mail dostawcy oprogramowania, przepisany
z treści komunikatu.

```html
<p>Telefon: <a href="tel:+48897550900">89&nbsp;755&nbsp;09&nbsp;00</a><br>
  Adres: ul. Kolejowa 2 lok. 208, 11-440 Reszel</p>
```

Gdyby numer się zmienił, trzeba poprawić go **w dwóch miejscach w tym samym wierszu**: w adresie
odnośnika (`tel:` — bez spacji, z numerem kierunkowym kraju `+48`) oraz w widocznym tekście
(zamiast spacji wstawiamy `&nbsp;`, żeby numer nie łamał się na dwa wiersze). Numer trzeba wtedy
zmienić także w treści SMS-a poniżej.

## Jak zaktualizować treść strony

1. Otwórz `index.html` w zwykłym edytorze tekstu (nie w Wordzie) albo bezpośrednio na GitHubie
   (przycisk z ołówkiem nad plikiem).
2. Zmień tylko tekst między znacznikami, np. między `<p>` a `</p>`. Nie zmieniaj samych znaczników.
3. **Zawsze dopisz datę aktualizacji.** Na dole pliku, w stopce, są dwa wiersze:

   ```html
   <p>Data publikacji: 9 października 2026.</p>
   <p>Ostatnia aktualizacja: 9 października 2026.</p>
   ```

   Datę publikacji zostaw bez zmian, a datę w drugim wierszu zmień na dzisiejszą.
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
Indywidualna Praktyka Stomatologiczna Mariola Krajewska: wazna informacja. Wpisz w przegladarce: gabinetkrajewska.github.io Tel. 897550900. Nie prosimy o dane.
```

To **159 znaków**. Cała wiadomość musi mieć najwyżej **160 znaków**, inaczej operator podzieli ją
na dwie wiadomości. Przy pełnej nazwie praktyki nie mieści się już numer telefonu zapisany ze
spacjami — stąd `897550900` bez spacji (telefony i tak rozpoznają taki numer i pozwalają na niego
zadzwonić jednym dotknięciem).

## Publikacja na GitHub Pages

Strona jest już opublikowana. Ustawienia (Settings → Pages): źródło **Deploy from a branch**,
gałąź `main`, katalog `/ (root)`, włączone **Enforce HTTPS**. Każdy `git push` do gałęzi `main`
aktualizuje stronę w ciągu około minuty.

Jeśli adres repozytorium kiedykolwiek się zmieni, trzeba poprawić adres w trzech miejscach:
w `index.html` (znacznik `og:url`), w tym pliku oraz w treści SMS-a.

## Podgląd lokalny

W katalogu z plikami:

```bash
python3 -m http.server 8000
```

Następnie w przeglądarce: `http://localhost:8000`.
