#Seguridad con jQuery

Lo adecuado es crear elementos DOM de forma programática e irlos insertando en el DOM. Esto significa que se debe evitar el uso de .html(), .innerHTML y otras funciones relacionadas, en su lugar es recomendable usar .append(), .prepend(), .before(), .after() y otras similares.

Por ejemplo:

```
1 |  jQuery.ajax({
2 |      url: 'http://unsitio.com/datos.json'
3 |  }).done( function( data ) {
4 |      var link = '<a href="' + data.url + '">' + data.title + '</a>';
5 |  jQuery( '#unDiv' ).html( link );
6 |  });
```
Esta aproximación puede ser peligrosa ya que estamos confiando en que la respuesta por parte de unsitio.com sólo incluye contenido seguro, algo que no podemos garantizar aún cuando el sitio sea nuestro. Cómo podemos asegurar que data.title no contiene:
```
1|<script type="text/javascript"> alert( "haxxored"); </script>;
```
En lugar de esto, la forma correcta sería crear un elemento DOM de forma programática y luego insertarlo en el DOM:
```
jQuery.ajax({
    url: 'http://unsitio.com/datos.json'
}).done( function( data ) {
    var a = jQuery( '' );
    a.attr( 'href', data.url );
    a.text( data.title );
    jQuery( '#unDiv' ).append( a );
});
```
Al pasar los datos a través de jQuery o de la API DOM del navegador, aseguramos que los valores están debidamente desinfectados y eliminamos la necesidad de inyectar snippets HTML inseguros en la página.

Para garantizar la seguridad de la aplicación, es recomendable usar la API DOM proporcionada por el navegador (o jQuery) para toda la manipulación DOM.