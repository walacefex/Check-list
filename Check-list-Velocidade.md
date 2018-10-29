### Check List Velocidade

* Cache no Navegador
* Minifique CSS, Javascript e HTML
* Não use Javascript de bloqueio de renderização, JS sempre no Footer - PLG Speed Booster Pack 
* GZIP - mod_deflate(Apache)
* GZIP Locaweb - https://wiki.locaweb.com.br/pt-br/Habilitar_Gzip_Deflate
* GZIP TEST - https://checkgzipcompression.com, https://www.giftofspeed.com/gzip-test/
* Cache Locaweb -  https://wiki.locaweb.com.br/pt-br/Habilitar_cache_via_htaccess
* Habilitar o Keep Alive - .htaccess, teste: curl -i url
* Otimize Imagens
* Remove version dos includes css e js
* CDN
* AMP  - Ferramenta facebook
* Instant Articles - Ferramenta facebook

# Adicionar Gzip no Servidor
Referência: https://www.eduardomaio.net/tornar-um-site-mais-rapido-com-compressao-gzip-e-brotli/
```
<IfModule mod_deflate.c>
  AddOutPutFilterByType DEFLATE text/html text/xml text/css text/javascript
</IfModule>
```
```
<IfModule mod_headers.c>
    # Make sure proxies don't deliver the wrong content
    # Header append Vary User-Agent env=!dont-vary
    Header set Connection keep-alive
    <FilesMatch ".(js|css|xml|gz|html|woff|woff2|otf|ttf)$">
        Header append Vary: Accept-Encoding
    </FilesMatch>
</IfModule>
```

# [Forçar Cache](https://github.com/Amarelo-Manga/Base-Conhecimento/blob/master/For%C3%A7a-a-utilizar-Cache-Control-e-Expires-header.md)

# Remover Versão dos scripts css e JS
```
// remove wp version param from any enqueued scripts
function vc_remove_wp_ver_css_js( $src ) {
    if ( strpos( $src, 'ver=' ) )
        $src = remove_query_arg( 'ver', $src );
    return $src;
}
add_filter( 'style_loader_src', 'vc_remove_wp_ver_css_js', 9999 );
add_filter( 'script_loader_src', 'vc_remove_wp_ver_css_js', 9999 );
````

# Adicionar Style Minify como padrão WP
```
function style_or_min_style( $stylesheet_uri, $stylesheet_dir_uri ) {
    $located = locate_template( 'style.min.css' );
	if ($located != '' ) {
	    return trailingslashit( $stylesheet_dir_uri ) . 'style.min.css';
	} else {
	   return trailingslashit( $stylesheet_dir_uri ) . 'style.css';
	}
}
add_filter( 'stylesheet_uri', 'style_or_min_style', 10, 2);
```

# [Dicas de otimização para WP](http://www.wpbeginner.com/wordpress-performance-speed/)

# [Verificar Informações do Servidor/Site - BrowserSpy](http://browserspy.dk/webserver.php)

# Ferramentas para testes
- [Verificar Velcidade do site Google Page Speed](https://developers.google.com/speed/pagespeed/insights/)
- [Verificar Velocidade do Site Pingdom](https://tools.pingdom.com/)
- [Verificar Velocidade do site GTmetrix](https://gtmetrix.com)
- [Verificar Velocidade do Site WebPagetest, com timeline visual](https://www.webpagetest.org)
- [Verificar Site no Mobile Google](https://search.google.com/test/mobile-friendly)
- [Verificar site no Mobile Geek Flare](https://tools.geekflare.com/)
- [Verficar Site no Mobile Dareboost](https://www.dareboost.com/en/mobile-website-speed-test)
- [Verificar GZIP Compression](https://checkgzipcompression.com)
- [Ferramentas para Otimização](https://www.giftofspeed.com/tools/)
- [Check Links Quebrados no site](https://www.deadlinkchecker.com/website-dead-link-checker.asp)
- [Check richview](https://richpreview.com)
