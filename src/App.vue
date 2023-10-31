<template>
  <header>
    <div class="logo">
      <svg xmlns="http://www.w3.org/2000/svg" width="42" height="42" viewBox="0 0 24 24"><path fill="currentColor" fill-rule="evenodd" d="M7 14a2 2 0 1 0 0-4a2 2 0 0 0 0 4Zm3.465-4a4.002 4.002 0 0 0-7.339 1H2a1 1 0 1 0 0 2h1.126A4.002 4.002 0 0 0 11 12h2a4 4 0 0 0 7.874 1H22a1 1 0 1 0 0-2h-1.126a4.002 4.002 0 0 0-7.339-1h-3.07ZM15 12a2 2 0 1 0 4 0a2 2 0 0 0-4 0Z" clip-rule="evenodd"/></svg>
      <p>Vue Reading Mode</p><span>Demo</span></div>
  </header>
  <main>
    <vue-reading-mode>
      <testarticle2></testarticle2>
    </vue-reading-mode>

    <vue-reading-mode>
      <testarticle></testarticle>
    </vue-reading-mode>

    <div class="copyright">
      <a href="https://github.com/BoraKucukkara/vue-reading-mode" title="Bora Kucukkara / vue-reading-mode on Github">
        <svg height="24" aria-hidden="true" viewBox="0 0 16 16" version="1.1" width="24" data-view-component="true" class="octicon octicon-mark-github v-align-middle">
          <path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
        </svg>
      </a>
      <a href="https://www.borakucukkara.com/" title="Bora Kucukkara personal web site">
        <img src="https://www.borakucukkara.com/borakucukkara.png" width="24">
      </a>
    </div>
  </main>
</template>
<script>
import testarticle from './components/testarticle.vue';
import testarticle2 from './components/testarticle2.vue';
import vueReadingMode from './components/vueReadingMode.vue'
export default {
  components: {
    vueReadingMode,
    testarticle,
    testarticle2
  }
}
</script>
<style>
header {
  background:rgb(211, 217, 218);
  display: grid;
  width: 100%;
}
.logo {
  width: auto;
  margin: 1rem 2rem;
  font-size: 1.4rem;
  font-weight: 700;
  color: #352f41;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}
.logo svg {
  color:tomato;
  padding-right: .5rem;
}
.logo span {
  color:rgb(121, 140, 150);
  font-weight: 300;
  padding-left: .5rem;
}
header nav {
  margin: 2rem 2rem;
}
main > * {
  max-width: 960px;
}
main article {
  border-bottom:1px solid #999;
  padding:0 0 2rem 0;
  margin:0 1rem 1rem 1rem;
}
#app {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  color:#444;
}
#app h1 {color:tomato}
#app h2 {color:coral}
#app h3 {color:lightsalmon}

.copyright { height: 2rem; width: 100%; text-align:center;}
.copyright a {padding: .3rem; opacity: .7; transition: all .3s;}
.copyright a:hover {opacity: 1}
</style>
