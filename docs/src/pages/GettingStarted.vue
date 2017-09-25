<template>
  <page-content page-title="Getting Started">
    <div class="main-content">
      <article>
        <section>
          <h2 class="md-headline">Include Fonts and Icons</h2>

          <p>Use Roboto and Google Icons from Google CDN:</p>
          <code-block lang="xml">
            &lt;link rel=&quot;stylesheet&quot; href=&quot;//fonts.googleapis.com/css?family=Roboto:300,400,500,700,400italic&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;//fonts.googleapis.com/icon?family=Material+Icons&quot;&gt;
          </code-block>
        </section>
      </article>

      <article>
        <h2 class="md-headline">Installation</h2>

        <section>
          <h3 class="md-title">NPM</h3>
          <p>Install Vue Material through npm or yarn <br><small>* Others package managers like JSPM and Bower are not supported yet.</small></p>
          <code-block lang="bash">
            $ npm install --save git+ssh://git@bitbucket.org/docutap/ui.git#1fe052f
            $ yarn add git+ssh://git@bitbucket.org/docutap/ui.git#1fe052f
          </code-block>
        </section>
      </article>

      <article>
        <h2 class="md-headline">Usage</h2>

        <section>
          <h3 class="md-title">AMD Modules</h3>

          <p>Import and use the whole library:</p>
          <code-block lang="xml">
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/ui.css&quot;&gt;
          </code-block>

          <code-block lang="javascript">
            var Vue = require('vue')
            var DocutapUi = require('@docutap/ui')

            Vue.use(DocutapUi)
          </code-block>

          <p>Or to import individual components:</p>
          <code-block lang="xml">
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/@docutap/ui/dist/components/mdCore.css&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/@docutap/ui/dist/components/mdButton.css&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/@docutap/ui/dist/components/mdIcon.css&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/@docutap/ui/dist/components/mdSidenav.css&quot;&gt;
            &lt;link rel=&quot;stylesheet&quot; href=&quot;path/to/@docutap/ui/dist/components/mdToolbar.css&quot;&gt;
          </code-block>

          <code-block lang="javascript">
            var Vue = require('vue')
            var DocutapUi = require('@docutap/ui')

            Vue.use(DocutapUi.mdCore) //Required to boot vue material
            Vue.use(DocutapUi.mdButton)
            Vue.use(DocutapUi.mdIcon)
            Vue.use(DocutapUi.mdSidenav)
            Vue.use(DocutapUi.mdToolbar)
          </code-block>

          <p><strong>Note:</strong> If you are using Webpack you can still import the css files inside your modules. And you can also write everything using ES6 with Babel or Bublé.</p>
        </section>
      </article>

      <article>
        <h2 class="md-headline">Codepen Examples</h2>

        <section>
          <h3 class="md-title">Playground</h3>
          <iframe height="620" scrolling="no" title="Empty Setup" src="//codepen.io/vue-material/embed/VmMrYW/?height=620&amp;theme-id=dark&amp;default-tab=html,result&amp;embed-version=2" frameborder="no" allowtransparency="true" allowfullscreen="true" style="width: 100%;">See the Pen <a href="http://codepen.io/vue-material/pen/VmMrYW/">Empty Setup</a> by Vue Material (<a href="http://codepen.io/vue-material">@vue-material</a>) on <a href="http://codepen.io">CodePen</a>.</iframe>
        </section>

        <section>
          <h3 class="md-title">File Application UI</h3>
          <iframe width="360" height="610" scrolling="no" title="File Application UI" src="//codepen.io/vue-material/embed/WoZpMR/?height=610&amp;theme-id=dark&amp;default-tab=result&amp;embed-version=2" frameborder="no" allowtransparency="true" allowfullscreen="true">See the Pen <a href="http://codepen.io/vue-material/pen/WoZpMR/">Vue Material Example</a> by Vue Material (<a href="http://codepen.io/vue-material">@vue-material</a>) on <a href="http://codepen.io">CodePen</a>.</iframe>
        </section>
      </article>
    </div>
  </page-content>
</template>

<style lang="scss" scoped>
  .main-content {
    position: relative;
  }

  article {
    max-width: 960px;
  }

  section + section,
  article + article {
    margin-top: 36px;
  }

  .code-block,
  .md-tabs {
    max-width: 100%;
  }

  .md-tab {
    border-top: 1px solid rgba(#000, .12);
    padding: 0;
  }

  iframe {
    height: auto;
    min-height: 620px;
  }
</style>
