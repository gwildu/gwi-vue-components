<template>
    <div class="markdown" v-html="content"/>
</template>

<script>
  import MarkdownIt from "markdown-it";
  import markdownItCheckbox from 'markdown-it-checkbox'
  const md = new MarkdownIt().use(markdownItCheckbox, {
    divWrap: true,
    divClass: 'checkbox'
  });
  export default {
    name: "GwiMarkdown",
    props: {
      markdown: {
        type: String,
        default: ""
      }
    },
    computed: {
      content() {
        return md.render(this.markdown)
      }
    },
    methods: {
      doSomething() {
        alert('something');
      }
    }
  };
</script>

<style lang="scss">
  @import './index';
  .markdown {
    h1, h2, h3, h4, p, blockquote, code, pre, img, ul, ol {
      margin-bottom: $markdown__spacing-bottom--default;
    }
    h1 {
      @include markdown__heading--1;
    }
    h2 {
      @include markdown__heading--2;
    }
    h3 {
      @include markdown__heading--3;
    }
    h4 {
      @include markdown__heading--4;
    }
    strong {
      @include markdown__inline--strong;
    }
    em {
      @include markdown__inline--em;
    }
    blockquote {
      @include markdown__blockquote;
      p {
        margin-bottom: 0;
      }
    }

    @include markdown__code;

    img {
      @include markdown__image;
    }
    ul {
      @include markdown__ul;
    }
    ol {
      @include markdown__ol;
    }

    @include markdown__checklist;
  }
  @include markdown__inline--a;

</style>
