// opciones
var option = {
	pageURL: 'https://www.byzeroblogger.com/',
	container: '.appjs-newsletter__post',
	length: 6,
	image: 's36-c',
	label: 'blogger',
	isPublished: true,
	isThumbnail: true,
	isSummary: true
}

# appjs-newsletter

> Sencillo boletín de noticias para blogger basado en los feed del blog.



## Estructura HTML

El siguiente html, puedes ubicarlo dónde gustes.

```html
<div class="appjs-newsletter">

	<div class="appjs-newsletter__left">
		<span class="appjs-newsletter__header">
			 <i class="fa fa-external-link-alt"></i> noticias
		</span>
	</div>

	<div class="appjs-newsletter__right">
		<ul class="appjs-newsletter__post" data-newsletterTime="3000">
			<span class="appjs-newsletter__info">Cargando...</span>
		</ul>
	</div>

</div>
```

## Estilos css

> dist/newsletter.min.css

## Javascript

Ubica el siguiente código javascript justo arriba de ```</body>``` en tu plantilla.

```html 
<script>
// opciones
var option = {
	pageURL: 'https://www.byzeroblogger.com/',
	container: '.appjs-newsletter__post',
	length: 6,
	image: 's36-c',
	label: 'blogger',
	isPublished: true,
	isThumbnail: true,
	isSummary: true
}

/*!
 * appjs-newsletter | v1.0.4
 * Copyright 2018 byzerblogger
 * Developed by Marcelo Toledo (KuroSensei)
 */

//<![CDATA[
"use strict";var appjsTicker=function(u){var e=u.createElement("script"),t=u.body;e.src=option.pageURL+"feeds/posts/default/-/"+option.label+"?alt=json-in-script&callback=appTicker&max-results="+option.length,t.appendChild(e),window.appTicker=function(e){var s,t,a,n,i,l,r,o,p=u.querySelector(option.container);p.innerHTML="";for(var c=0;c<e.feed.entry.length;c++)p.innerHTML+=(s=e.feed.entry[c],t=c,o=i=void 0,a=s.title.$t,n=s.media$thumbnail.url.replace("s72-c",option.image),i=s.summary?s.summary.$t:s.content.$t.replace(/<[^>]*>?/g,""),l=function(){for(var e=0;e<s.link.length;e++){var t=s.link[e];if("alternate"===t.rel)return t.href}}(),r=new Date(s.published.$t).toLocaleDateString("es-ES"),o="",o+='<li class="appjs-newsletter__item '+(0==t?"active":"")+'">',o+=option.isThumbnail?'<div class="appjs-newsletter__thumbnail"><img src="'+n+'" alt="'+a+'"></div>':"",o+='<div class="appjs-newsletter__contain">',o+='<a href="'+l+'" class="appjs-newsletter__title" title="'+a+'">'+a+" "+(option.isPublished?'<span class="appjs-newsletter__meta">'+r+"</span>":"")+"</a>",o+=option.isSummary?'<span class="appjs-newsletter__summary">'+(54<i.length?i.substr(0,54)+"...":i)+"</span>":"",o+="</div>",o+="</li>");!function(){function e(e,t){for(var s=document.querySelectorAll(e),a=0;a<s.length;a++)s[a].classList.remove(t)}var t=u.querySelectorAll(".appjs-newsletter__post li"),s=u.querySelector(".appjs-newsletter__post"),a=s.getAttribute("data-newsletterTime"),n=0,i=setInterval(function(){++n>t.length-1&&(n=0),e(".appjs-newsletter__post li","active"),t[n].classList.add("active")},a);s.addEventListener("mouseover",function(){clearInterval(i),e(".appjs-newsletter__post li","active"),t[n].classList.add("active")}),s.addEventListener("mouseout",function(){i=setInterval(function(){++n>t.length-1&&(n=0),e(".appjs-newsletter__post li","active"),t[n].classList.add("active")},a)})}()}}(document);
//]]>
</script>
```

### opciones

Las opciones están basados en un objeto de javascript y es necesario declararlas antes del código principal. En la siguiente tabla
se detallan sus atributos disponibles.

Nombre | Tipo | Explicación
------------ | -------------| -------------
pageURL | String | URL del blog
container | String | Selector css válido para insertar las entradas generadas
length | Number | Cantidad de post a mostrar
image | String | Tamaño de la imagen en formato aceptado por blogger
label | String | Etiqueta de alguna entrada
isPublished | Boolean | Nos permite mostrar u ocultar la fecha de públicación de las entradas, por defecto es true
isThumbnail | Boolean | Nos permite mostrar u ocultar la miniatura de las entradas, por defecto es true
isSummary | Boolean | Nos permite mostrar u ocultar el resumen de las entradas, por defecto es true

#### License

**appjs-newsletter** is licensed under the MIT License.