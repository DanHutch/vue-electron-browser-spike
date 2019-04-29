<template>
  <div id="browse-container">
    {{src}}
    <webview ref="wvref" id="browse" src="https://duckduckgo.com"></webview>
  </div>
</template>

<script>
export default {
  data: () => ({
    webview: {},
    src: "https://duckduckgo.com"
  }),
  computed: {
  },
  watch: {
    src: {
      handler: function() {
        console.log("watcher for webview hit!");
      }
    }
  },
  mounted() {
    let wv = this.webview;
    this.webview = document.querySelector("webview");
    console.log(this.webview);
    this.webview.addEventListener("did-stop-loading", this.updateWebview);
  },
  methods: {
    updateWebview(event) {
      this.src = event.target.src;
      console.log(this.src);
    }
  }
};
</script>

<style>
#browse {
  height: 100%;
  width: 100%;
}

#browse-container {
  height: 100%;
  width: 100%;
}
</style>
