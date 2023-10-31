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
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
}
.logo {
  width: max-content;
margin: 1rem 2rem;
font-size: 1.4rem;
font-weight: 700;
color: #352f41;
display: flex;
align-items: center;
flex-direction: row;
}
.logo * {margin: 0; line-height: 1;}
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
  margin:6rem 1rem;
  border-bottom: 1px solid #ccc;
  max-width: 960px;
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
</style>
