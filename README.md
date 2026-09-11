# Baza herbów

Ten folder przechowuje herby drużyn, które można wybrać bezpośrednio na stronie
(przycisk "📁 Wybierz z bazy" przy sekcji herbów w obu generatorach).

## Jak dodać nowy herb (bez edytowania żadnego pliku)

1. Wrzuć plik PNG / JPG / SVG (najlepiej z przezroczystym tłem) do tego folderu,
   np. `herby/legia_warszawa.png`.
2. Zrób commit i push do GitHuba.
3. Gotowe — po odświeżeniu strony herb pojawi się automatycznie w oknie wyboru.
   Nie trzeba nigdzie ręcznie wpisywać nazwy pliku.

Strona sama pobiera listę plików z tego folderu przez publiczne GitHub API
(`api.github.com/repos/.../contents/herby`), więc wystarczy sama obecność
pliku w repozytorium.

## Nazewnictwo plików

Nazwa pliku (bez rozszerzenia) jest pokazywana jako etykieta pod herbem
w oknie wyboru, z zamianą `_` i `-` na spacje. Warto więc nazywać pliki
czytelnie, np. `wisla_krakow.png` zamiast `img1.png` — ułatwia to też
wyszukiwanie w okienku.

## Ograniczenia

- Lista jest cache'owana w przeglądarce na 5 minut (żeby nie odpytywać
  GitHub API przy każdym otwarciu okienka) — jeśli dodasz nowy herb i od
  razu chcesz go zobaczyć, odśwież stronę z wyczyszczoną pamięcią podręczną
  (Ctrl/Cmd+Shift+R) albo poczekaj kilka minut.
- Podfoldery wewnątrz `herby/` nie są przeszukiwane — trzymaj pliki płasko,
  bezpośrednio w tym folderze.
- Jeśli strona jest wystawiona pod WŁASNĄ domeną (nie `*.github.io`),
  automatyczne wykrycie właściciela/nazwy repozytorium może zawieść.
  W takim wypadku otwórz plik `PODSUMOWANIE_MECZY.html` / `ZAPOWIEDZI_MECZOWE.html`,
  znajdź w kodzie sekcję:
  ```js
  const CREST_MANUAL_OWNER = '';
  const CREST_MANUAL_REPO = '';
  ```
  i wpisz tam ręcznie nazwę użytkownika GitHub oraz nazwę repozytorium.
- Jeśli GitHub API z jakiegoś powodu zawiedzie (limit zapytań, offline itp.),
  strona spróbuje jeszcze wczytać opcjonalny plik `herby/manifest.json`
  (lista nazw plików w formacie `["plik1.png", "plik2.png"]`) — to tylko
  zapasowa metoda, nie trzeba go utrzymywać.
- Testowanie lokalne przez otwarcie pliku `.html` dwuklikiem (`file://`)
  nie zadziała — strona musi być wystawiona przez serwer (GitHub Pages
  albo lokalny serwer HTTP).
