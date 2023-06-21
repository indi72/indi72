Ext News Partner

&nbsp;

**Installieren**

\typo3conf\ext\news_partner\

&nbsp;

**Dateien**

\typo3conf\ext\theme\Resources\Private\ext\news\Partials\List\Partner.html

\typo3conf\ext\theme\Resources\Private\ext\news\Templates\NewsList.html

\typo3conf\ext\theme\Resources\Private\ext\news\Templates\News\Detail.html

\typo3conf\ext\theme\Resources\Private\ext\news\Templates\News\SearchResult.html

\typo3conf\ext\theme\Resources\Public\js\newsPartner.js

&nbsp;

**Anpassen**

_Auskommentieren in YouTubeRenderer.php und VimeoRenderer.php_

\typo3conf\ext\we_cookie_consent\Classes\Resource\Rendering\YouTubeRenderer.php

\typo3conf\ext\we_cookie_consent\Classes\Resource\Rendering\VimeoRenderer.php

```
public function render ( ... ) { ... }
```

&nbsp;

_Code in jquery-ias.js einfügen_

\typo3conf\ext\infinitescrolling\Resources\Public\JavaScript\Ias\jquery-ias.js

```
// Funktion zum Laden der JavaScript-Datei, Warten und Einblenden des Inhalts
function loadCustomJSAndShow() {
    $(items).hide(); // zunächst ausblenden, um es später einzublenden
    // Laden der JavaScript-Datei
    var script = document.createElement('script');
    script.src = '/typo3conf/ext/theme/Resources/Public/js/newsPartner.js';
    script.onload = function() {
        console.log("newsPartner.js geladen");
        
        // Einblenden des Inhalts mit Animation
        $(items).fadeIn(400, function() {
            // Anzeigen des Inhalts
            $(items).css('display', 'block');

            // complete callback get fired for each item,
            // only act on the last item
            if (++count < items.length) {
                return;
            }

            self.fire('rendered', [items]);

            if (callback) {
                callback();
            }
        });
    };
    document.head.appendChild(script);
}
```
