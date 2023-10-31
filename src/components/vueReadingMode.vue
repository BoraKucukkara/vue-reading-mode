<template>
    <div class=""
    :style="{ '--vrm-font-family': fontFamily,
              '--vrm-font-multiplier': fontsize,
              '--vrm-line-height': lineHeight,
              '--vrm-width-multiplier': widthMultiplier}"
    :class="{'reader-mode--fullscreen':fullscreen && readingmode,
            'reader-mode--dark':theme == 'dark' && readingmode,
            'reader-mode--light':theme == 'light' && readingmode,
            'reader-mode': readingmode
            }">
        <nav class="reader-mode--nav">
            <div v-if="readingmode" @click="themeSelect('dark')">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" d="M12 3a9 9 0 1 0 9 9c0-.46-.04-.92-.1-1.36a5.389 5.389 0 0 1-4.4 2.26a5.403 5.403 0 0 1-3.14-9.8c-.44-.06-.9-.1-1.36-.1z"/></svg>
                <span v-if="theme == 'dark'" class="reader-mode--nav-dot"></span>
            </div>
            <div v-if="readingmode" @click="themeSelect('light')">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" d="M12 9c1.65 0 3 1.35 3 3s-1.35 3-3 3s-3-1.35-3-3s1.35-3 3-3m0-2c-2.76 0-5 2.24-5 5s2.24 5 5 5s5-2.24 5-5s-2.24-5-5-5zM2 13h2c.55 0 1-.45 1-1s-.45-1-1-1H2c-.55 0-1 .45-1 1s.45 1 1 1zm18 0h2c.55 0 1-.45 1-1s-.45-1-1-1h-2c-.55 0-1 .45-1 1s.45 1 1 1zM11 2v2c0 .55.45 1 1 1s1-.45 1-1V2c0-.55-.45-1-1-1s-1 .45-1 1zm0 18v2c0 .55.45 1 1 1s1-.45 1-1v-2c0-.55-.45-1-1-1s-1 .45-1 1zM5.99 4.58a.996.996 0 0 0-1.41 0a.996.996 0 0 0 0 1.41l1.06 1.06c.39.39 1.03.39 1.41 0s.39-1.03 0-1.41L5.99 4.58zm12.37 12.37a.996.996 0 0 0-1.41 0a.996.996 0 0 0 0 1.41l1.06 1.06c.39.39 1.03.39 1.41 0a.996.996 0 0 0 0-1.41l-1.06-1.06zm1.06-10.96a.996.996 0 0 0 0-1.41a.996.996 0 0 0-1.41 0l-1.06 1.06c-.39.39-.39 1.03 0 1.41s1.03.39 1.41 0l1.06-1.06zM7.05 18.36a.996.996 0 0 0 0-1.41a.996.996 0 0 0-1.41 0l-1.06 1.06c-.39.39-.39 1.03 0 1.41s1.03.39 1.41 0l1.06-1.06z"/></svg>
                <span v-if="theme == 'light'" class="reader-mode--nav-dot"></span>
            </div>
            <hr  v-if="readingmode" class="reader-mode--seperator">
            <div v-if="readingmode" @click="fontType('sans-serif')">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="16" viewBox="0 0 512 512"><path fill="currentColor" d="M32 256h192v64h-64v192H96V320H32zm448-128H354.125v384h-68.25V128H160V64h320z"/></svg>
                <span v-if="fontFamily == 'sans-serif'" class="reader-mode--nav-dot"></span>
            </div>
            <div v-if="readingmode" @click="fontType('serif')">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="16" viewBox="0 0 512 512"><path fill="currentColor" d="M145.569 399.818c.732 27.217 3.468 34.081 37.52 36.527v20.732H61.654v-20.732c34.052-2.446 37.792-9.31 38.524-36.527l-.022-169.31c-56.744-1.92-66.1 10.1-74.69 49.172H0c4.936-22.375 9.824-43.73 9.824-74.393H235.9c0 30.664 2.469 52.018 7.405 74.393H218.35c-8.59-39.072-16.038-51.092-72.782-49.173v169.31m237.546-5.153c.833 21.807 11.216 35.575 50.003 37.534v24.879H282.343v-24.879c38.786-1.96 48.237-15.728 49.07-37.535l-.025-306.284c-72.995-1.738-93.062 6.565-99.274 56.01h-29.61c6.341-25.487 5.36-54.54 5.36-89.466h294.623c0 34.927 3.171 63.98 9.513 89.465h-32.06c-11.037-44.504-32.192-58.196-96.825-56.01v306.285"/></svg>
                <span v-if="fontFamily == 'serif'" class="reader-mode--nav-dot"></span>
            </div>
            <hr  v-if="readingmode" class="reader-mode--seperator">
            <div v-if="readingmode" @click="fontSizeDecrease()">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" d="M.99 19h2.42l1.27-3.58h5.65L11.59 19h2.42L8.75 5h-2.5L.99 19zm4.42-5.61L7.44 7.6h.12l2.03 5.79H5.41zM23 11v2h-8v-2h8z"/></svg>
            </div>
            <div v-if="readingmode" @click="fontSizeIncrease()">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" d="M.99 19h2.42l1.27-3.58h5.65L11.59 19h2.42L8.75 5h-2.5L.99 19zm4.42-5.61L7.44 7.6h.12l2.03 5.79H5.41zM20 11h3v2h-3v3h-2v-3h-3v-2h3V8h2v3z"/></svg>
            </div>
            <hr  v-if="readingmode" class="reader-mode--seperator">
            <div v-if="readingmode" @click="lineHeightSetter(1.2)">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 72 72"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-miterlimit="10" stroke-width="2" d="M16 26h40M16 36h40M16 46h40"/></svg>
                <span v-if="lineHeight == 1.2" class="reader-mode--nav-dot"></span>
            </div>  
            <div v-if="readingmode" @click="lineHeightSetter(1.4)">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" d="M3 6.001h18m-18 6h18m-18 6h18"/></svg>
                <span v-if="lineHeight == 1.4" class="reader-mode--nav-dot"></span>
            </div>
            <div v-if="readingmode" @click="lineHeightSetter(1.6)">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" d="M3.563 4.063a.5.5 0 0 1 0-1l16.874-.001a.5.5 0 0 1 0 1l-16.874.001Zm0 8.438a.5.5 0 0 1 0-1l16.874-.002a.5.5 0 0 1 0 1l-16.874.002Zm0 8.438a.5.5 0 0 1 0-1l16.874-.002a.5.5 0 0 1 0 1l-16.874.002Z"/></svg>
                <span v-if="lineHeight == 1.6" class="reader-mode--nav-dot"></span>
            </div>
            <hr  v-if="readingmode" class="reader-mode--seperator">
            <!--<div v-if="readingmode" @click="fullscreenToggler()">
                <svg v-if="!fullscreen" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20"><path fill="currentColor" d="M7 2H2v5l1.8-1.8L6.5 8L8 6.5L5.2 3.8L7 2zm6 0l1.8 1.8L12 6.5L13.5 8l2.7-2.7L18 7V2h-5zm.5 10L12 13.5l2.7 2.7L13 18h5v-5l-1.8 1.8l-2.7-2.8zm-7 0l-2.7 2.7L2 13v5h5l-1.8-1.8L8 13.5L6.5 12z"/></svg>
                <svg v-if="fullscreen" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20"><path fill="currentColor" d="M3.4 2L2 3.4l2.8 2.8L3 8h5V3L6.2 4.8L3.4 2zm11.8 4.2L18 3.4L16.6 2l-2.8 2.8L12 3v5h5l-1.8-1.8zM4.8 13.8L2 16.6L3.4 18l2.8-2.8L8 17v-5H3l1.8 1.8zM17 12h-5v5l1.8-1.8l2.8 2.8l1.4-1.4l-2.8-2.8L17 12z"/></svg>
            </div>-->
            <div @click="readingModeToggle()">
                <svg v-if="readingmode" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" fill-rule="evenodd" d="M15 3.001a1 1 0 1 1 0 2H6v13a1 1 0 0 0 1 1h8a1 1 0 1 1 0 2H7a3 3 0 0 1-3-3v-14a1 1 0 0 1 1-1h10Zm1.707 5.293A1 1 0 0 0 15 9v2H9a1 1 0 1 0 0 2h6v2a1 1 0 0 0 1.707.707l3-3a1 1 0 0 0 0-1.414l-3-3Z" clip-rule="evenodd"/></svg>
            </div>
        </nav>
        <article>
            <div @click="readingModeToggle()"
            :class="{'reader-mode--toggle': !readingmode}">
                <svg v-if="!readingmode" style="color:tomato" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path fill="currentColor" fill-rule="evenodd" d="M7 14a2 2 0 1 0 0-4a2 2 0 0 0 0 4Zm3.465-4a4.002 4.002 0 0 0-7.339 1H2a1 1 0 1 0 0 2h1.126A4.002 4.002 0 0 0 11 12h2a4 4 0 0 0 7.874 1H22a1 1 0 1 0 0-2h-1.126a4.002 4.002 0 0 0-7.339-1h-3.07ZM15 12a2 2 0 1 0 4 0a2 2 0 0 0-4 0Z" clip-rule="evenodd"/></svg>
                <p v-if="!readingmode">View in Reading Mode</p>
            </div>
            <!-- Main Content -->
                <slot/> 
            <!-- Main Content -->
        </article>
        <nav class="reader-mode--nav">
            <div @click="readingModeToggle()"
            :class="{'reader-mode--toggle': readingmode}">
                <svg v-if="readingmode" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path fill="currentColor" fill-rule="evenodd" d="M15 3.001a1 1 0 1 1 0 2H6v13a1 1 0 0 0 1 1h8a1 1 0 1 1 0 2H7a3 3 0 0 1-3-3v-14a1 1 0 0 1 1-1h10Zm1.707 5.293A1 1 0 0 0 15 9v2H9a1 1 0 1 0 0 2h6v2a1 1 0 0 0 1.707.707l3-3a1 1 0 0 0 0-1.414l-3-3Z" clip-rule="evenodd"/></svg>
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                readingmode: false,
                fontFamily:"serif",
                theme: "dark",
                fontsize: 1,
                widthMultiplier: 1,
                lineHeight: 1.4,
                fullscreen: true
            }
        },
        methods: {
            readingModeToggle() {
                this.readingmode = !this.readingmode
                if(this.readingmode == false) {
                    this.fontsize = 1
                    this.lineHeight = 1.4
                } 
            },
            fontSizeIncrease() {
                if(this.fontsize > 2) {
                    return
                } else {
                    this.fontsize += 0.1
                    this.widthMultiplier += 0.05
                }
            },
            fontSizeDecrease() {
                if(this.fontsize < 0.7) {
                    return
                } else {
                    this.fontsize -= 0.1
                    this.widthMultiplier -= 0.05
                }
            },
            themeSelect(type) {
                this.theme = type
            },
            fontType(type) {
                this.fontFamily = type
            },
            lineHeightSetter(size) {
                this.lineHeight = size
            },
            //fullscreenToggler() {
            //    this.fullscreen = !this.fullscreen
            //}

        }
        
    }
</script>

<style>
.reader-mode {
    --vrm-font-size: 1rem;
    --vrm-line-height: 1.4;
    --vrm-font-multiplier: 1;
    --vrm-font-family: serif;
    --vrm-width-multiplier: 1;

    max-width: 100vw !important;
    min-width: 300px;
    
    font-size: calc(var(--vrm-font-size) * var(--vrm-font-multiplier)) !important;
    font-family: var(--vrm-font-family) !important;
    font-size-adjust: .5;
    font-synthesis: none;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    -webkit-text-size-adjust: 100%;

    text-align: left !important;
    line-height: var(--vrm-line-height) !important;

    margin:0 !important;
    padding:3rem 2rem !important;

    z-index: 999999999 !important;
    overflow-y: auto;
    
    display: flex !important;
    flex-direction: column;
    justify-content: start !important;
    align-items: center;
}
.reader-mode article {
    max-width: calc(599px * var(--vrm-width-multiplier) )!important;
    height: auto;
    position: static !important;
    border-bottom:1px dashed #999 !important;
}
@media screen and (width < 600px) {
    .reader-mode {
        padding:2rem 1rem !important;
        width: calc(100vw - 2rem) !important;
    }
        .reader-mode *  {
            max-width: calc(100vw - 2rem) !important;
        }
    }
/* Reading Themes */
.reader-mode--dark, .reader-mode--dark * {
    fill: #E5EEFE !important;
    color: #E5EEFE !important;
    background-color:#1D1E21 !important;
    color-scheme: dark !important;
}
.reader-mode--light, .reader-mode--light * {
    fill: #36383B !important;
    color: #36383B !important;
    background-color:#EFF1F2 !important;
    color-scheme: light !important;
}
.reader-mode--dark a, .reader-mode--dark a:hover {
  font-weight: 500;
  color: #60aafa !important;
  text-decoration: underline;
}
.reader-mode--light a, .reader-mode--light a:hover {
  font-weight: 500;
  color: #1673d7 !important;
  text-decoration: underline !important;
}

/* Fullscreen Mode */
.reader-mode--fullscreen {
    position: fixed !important;
    inset: 0 !important;
    z-index: 999999999 !important;
    overflow-y: scroll !important;
}

/* Reading Mode Toggle */
.reader-mode--toggle {
    margin-top: 2rem;
    padding: .1rem .5rem;
    display: inline-flex;
    align-items: center;
    cursor: pointer;
    border-radius: 1rem;
    background: #f1f1f1 !important;
}
.reader-mode--toggle p {
    font-size: .8rem;
    margin:0 0 0 .5rem;
}
.reader-mode--toggle svg {
    width: 22px;
    height: 22px;
    margin: 0;
    color: #666;
    fill: #666;
}
.reader-mode--toggle:hover {
    background: #e3e3e3 !important;
}

/* Element options */
.reader-mode p {
    text-indent: 1.7rem !important;
}
.reader-mode * :not(h1, h2, h3, h4, h5, h6) {
    font-size: calc(1.3rem * var(--vrm-font-multiplier)) !important
}
.reader-mode h1 {
    font-size: calc(2.1rem * var(--vrm-font-multiplier)) !important;
    margin:2rem 0 1rem 0 !important;
}
.reader-mode h2 {
    font-size: calc(1.6rem * var(--vrm-font-multiplier)) !important;
    margin:2rem 0 .5rem 0 !important;
}
.reader-mode h3, .reader-mode h4,.reader-mode h5,.reader-mode h6 {
    font-size: calc(1.4rem * var(--vrm-font-multiplier)) !important;
    margin:1rem 0 .5rem 0 !important;
}
.reader-mode img, picture, video, audio, source, canvas,
             form, input, textarea, select, button, search,
            iframe, object {
    display: none !important;
}
.reader-mode code > *, .reader-mode pre > *, .reader-mode pre, .reader-mode code {
    font-size: calc(1rem * var(--vrm-font-multiplier)) !important;
    max-width: 100% !important;
    overflow:auto !important;
}

/* Navigation */
.reader-mode .reader-mode--nav {
    position: relative !important;
    display: flex;
    flex-direction: row;
    gap: .5rem;
    margin: 0 0 !important; 
}
.reader-mode .reader-mode--nav > div > svg {
    fill: #E5EEFE;
    opacity: .8;
    background: none !important;
}
.reader-mode .reader-mode--nav div {
    cursor: pointer;
    width: 24px;
    height: 24px;
    padding: 0 !important;
    margin: 0 !important;
    border-radius: 16px;
    display: grid;
    place-items: center;
    position: relative !important;
    background: none !important;
}
.reader-mode .reader-mode--nav div .reader-mode--nav-dot {
    position: absolute !important;
    pointer-events: none;
    background: none !important;
    opacity: .5;
    border-bottom: 1px solid ;
    top:1.6rem;
    width: .5rem;
}
.reader-mode .reader-mode--nav > div:hover {
    background: #66666650 !important;
}
.reader-mode--seperator {
    width: 1px;
    height: 28px;
    border:none;
    padding: 0;
    margin: 0;
    background: #77777740 !important;
}

/* Other adjustments */
.reader-mode ol, ul {
    padding-left:2rem !important;
    margin: 1rem 0 !important
}
.reader-mode ul {list-style:disc !important;}
.reader-mode ol {list-style:decimal !important;}
.reader-mode blockquote{
    border-left:.15rem solid #66666650 !important;
    margin: .5rem 0 !important;
    padding:0 1rem !important;
    font-style: italic !important;
    position: relative;
}
.reader-mode q {font-style: italic !important;}
</style>