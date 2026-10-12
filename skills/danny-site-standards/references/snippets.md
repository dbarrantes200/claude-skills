# Code snippets for danny-site-standards

Copy-paste building blocks. Adapt key names and values per site.

## GA4 snippet (in `<head>`)

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-5VGT1LL1V7"></script>
<script>
window.dataLayer = window.dataLayer || [];
function gtag(){dataLayer.push(arguments);}
gtag('js', new Date());
gtag('config', 'G-5VGT1LL1V7');
</script>
```

## i18n skeleton

```html
<div class="lang">
  <button id="lang-es">ES</button>
  <button id="lang-en">EN</button>
</div>
<h1 data-i18n="hero_h1"></h1>
<script>
const I18N = {
  es: { hero_h1: "Tu título en español" },
  en: { hero_h1: "Your headline in English" }
};
function setLang(l){
  localStorage.setItem('site-locale', l);
  document.documentElement.lang = l;
  document.querySelectorAll('[data-i18n]').forEach(el => {
    const k = el.getAttribute('data-i18n');
    if (I18N[l][k] !== undefined) el.innerHTML = I18N[l][k];
  });
  document.getElementById('lang-es').classList.toggle('on', l === 'es');
  document.getElementById('lang-en').classList.toggle('on', l === 'en');
}
document.getElementById('lang-es').onclick = () => setLang('es');
document.getElementById('lang-en').onclick = () => setLang('en');
setLang(localStorage.getItem('site-locale') || 'es');
</script>
```

## Reveal on scroll + hover lift

```css
.reveal { opacity: 0; transform: translateY(26px); transition: opacity .7s ease, transform .7s ease; }
.reveal.in { opacity: 1; transform: none; }
.card { transition: transform .25s ease, box-shadow .25s ease; }
.card:hover { transform: translateY(-4px); }
@media (prefers-reduced-motion: reduce) {
  .reveal { opacity: 1; transform: none; transition: none; }
  .card:hover { transform: none; }
}
```

```js
const io = new IntersectionObserver(es => es.forEach(e => {
  if (e.isIntersecting) { e.target.classList.add('in'); io.unobserve(e.target); }
}), { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => io.observe(el));
```

## AdSense placeholder slot

```html
<div class="ad-slot" data-ad-slot="PENDIENTE"></div>
```

## COUNTRY_LINKS skeleton

```js
const COUNTRY_LINKS = {
  US: { "tb-amz-11": "https://www.amazon.com/dp/XXXX?tag=tipsbici-20" },
  CA: {}, CL: {}, CR: {} // fall back to US until Danny provides links
};
function affUrl(key){
  const c = (localStorage.getItem('site-country') || 'US').toUpperCase();
  return (COUNTRY_LINKS[c] && COUNTRY_LINKS[c][key]) || COUNTRY_LINKS.US[key];
}
document.querySelectorAll('a[data-aff]').forEach(a => { a.href = affUrl(a.dataset.aff); });
```
