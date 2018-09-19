# appjs-newsletter

> Sencillo boletín de noticias para blogger basado en los feed del blog.



## Estructura HTML

El siguiente html, puedes ubicarlo dónde gustes.

```html
<div class="appjs-newsletter">
	<div class="appjs-newsletter__left">
		<span class="appjs-newsletter__header">
			 Noticias
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

Via rawgit.com

```html
<link rel="stylesheet" type="text/css" href="https://cdn.rawgit.com/KuroSensei/appjs-newsletter/69655826/dist/newsletter.min.css">
```

o bien:

```html
<style>
@charset "UTF-8";
/*! appjs-newsletter v1.0 © 2018 */
.appjs-newsletter{background:#fff;color:rgba(0, 0, 0, 0.7);display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-box-align:center;-ms-flex-align:center;align-items:center;overflow-x:hidden}.appjs-newsletter__header{background:#05C46B;color:#fff;padding:16px;font-weight:500;display:-webkit-box;display:-ms-flexbox;display:flex;font-size:14px;-webkit-box-align:center;-ms-flex-align:center;align-items:center;-webkit-box-pack:center;-ms-flex-pack:center;justify-content:center;position:relative}.appjs-newsletter__header i{margin-right:8px;display:inline-block;vertical-align:middle}.appjs-newsletter__header svg{width:24px;height:24px;fill:#fff}.appjs-newsletter__info{padding:0 32px;display:block;font-weight:500;font-size:14px;color:rgba(0, 0, 0, 0.5)}.appjs-newsletter__right{width:100%}.appjs-newsletter__post{margin:0;padding:0}.appjs-newsletter__item{padding:0 16px;list-style:none;display:none}.appjs-newsletter__item.active{display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-animation:1s jump forwards;animation:1s jump forwards}.appjs-newsletter__thumbnail{width:36px;height:36px}.appjs-newsletter__thumbnail img{width:100%;height:100%;border-radius:50%}.appjs-newsletter__contain{width:calc(100% - 36px);padding:0 16px}.appjs-newsletter__title{width:calc(100% - 36px);font-size:14px;text-decoration:none;color:rgba(0, 0, 0, 0.75);font-weight:500;padding-right:32px;padding-bottom:4px;-o-text-overflow:ellipsis;text-overflow:ellipsis;overflow:hidden;white-space:nowrap;display:block;-webkit-transition:all .3s;-o-transition:all .3s;transition:all .3s}.appjs-newsletter__title:hover{color:#05C46B}.appjs-newsletter__summary{width:calc(100% - 36px);font-size:12px;text-decoration:none;color:rgba(0, 0, 0, 0.45);font-weight:500;padding-right:16px;-o-text-overflow:ellipsis;text-overflow:ellipsis;overflow:hidden;white-space:nowrap;display:block}.appjs-newsletter__meta{background:#f5f5f5;color:rgba(0, 0, 0, 0.5);font-size:8px;line-height:normal;border-radius:4px;margin:0 8px;display:inline-block;vertical-align:middle;padding:3px}@-webkit-keyframes jump{0%{opacity:0}to{opacity:1}}@keyframes jump{0%{opacity:0}to{opacity:1}}

</style>
```

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
 * appjs-newsletter | v1.0
 * Copyright 2018 byzerblogger (github.com/KuroSensei/appjs-newsletter/blob/master/LICENSE)
 * Developed by Marcelo Toledo
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