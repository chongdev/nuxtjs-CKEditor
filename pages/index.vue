<template>

  <div class="container my-5 mx-auto max-width[600px]">

    <client-only> client

      <ckeditor-nuxt v-model="editorInput" :config="editorConfig" />
    </client-only>

    <!-- <ckeditor :editor="editor" :config="editorConfig" v-model="editorInput" /> -->
    <!-- @input="event => $emit('input', event)" -->
    <div class="mt-3">
      <h2>Preview</h2>
      <div class="ckeditor-preview" v-html="editorInput"></div>
    </div>
  </div>
</template>

<script>
// import CKEditor from '@ckeditor/ckeditor5-vue2';
// import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
// import FullFreeBuildEditor from '@blowstack/ckeditor5-full-free-build';
// import Editor from 'ckeditor5-custom-build/build/ckeditor';

// let FullFreeBuildEditor;
// let CKEditor;
// if (process.client) {
//   FullFreeBuildEditor = require('@blowstack/ckeditor5-full-free-build');
//   CKEditor = require('@ckeditor/ckeditor5-vue2')
// }else {
//   CKEditor = { component : {template:'<div></div>'}}
// }
export default {
  name: 'IndexPage',
  components: {
    // editor: Editor,
    // ckeditor: CKEditor,
    'ckeditor-nuxt': () => { if (process.client) { return import('@blowstack/ckeditor-nuxt') } },
  },

  data() {
    return {
      // editor: ClassicEditor,
      editorConfig: {
        width: 'auto',
        height: 630,

        simpleUpload: {
          uploadUrl: process.env.MEDIA_UPLOAD_URL,
        },

        // https://github.com/blowstack/ckeditor-nuxt

        ckbox: {
          tokenUrl: process.env.ckeditorToken
        },

        // plugins: ['Image', 'ImageCaption', 'ImageStyle', 'ImageToolbar', 'ImageUpload', 'MediaEmbed', 'MediaEmbedToolbar', 'Table'],
        removePlugins: [
          'ExportPdf',
          'ExportWord',
          // 'Title',
          // 'EasyImage',
          'RealTimeCollaborativeComments',
          'RealTimeCollaborativeTrackChanges',
          'RealTimeCollaborativeRevisionHistory',
          'PresenceList',
          'Comments',
          'TrackChanges',
          'TrackChangesData',
          'RevisionHistory',
          'Pagination',
          'WProofreader',
          'MathType',
        ],
        // removePlugins: [
        //   'Title', 

        //   // 'ListStyle', 
        //   // 'BlockQuote', 

        //   'FontBackgroundColor', 
        //   'FontColor', 
        //   'FontFamily', 
        //   'FontSize', 

        //   'Heading', 
        //   'Highlight', 

        //   // 'Indent',
        //   // 'IndentBlock',

        //   // 'HorizontalLine',

        //   // 'AutoImage',
        //   // 'LinkImage',
        //   // 'SimpleUploadAdapter',

        //   // 'SpecialCharacters',
        //   // 'SpecialCharactersArrows',
        //   // 'SpecialCharactersCurrency',
        //   // 'SpecialCharactersEssentials',
        //   // 'SpecialCharactersLatin',
        //   // 'SpecialCharactersMathematical',
        //   // 'SpecialCharactersText',

        //   'PageBreak',
        //   'Paragraph',
        //   'List',
        //   'ListStyle',

        //   'MathType',
        //   // 'MediaEmbed',
        //   // 'MediaEmbedToolbar',

        //   // 'PasteFromOffice',
        //   // 'RemoveFormat',

        //   'Subscript',
        //   'Superscript',

        //   'TextTransformation',
        //   'TodoList',

        //   'WordCount',

        //   // 'Underline',
        //   // 'Italic',
        //   // 'Strikethrough',
        // ],
        // removeDialogTabs: ['link:advanced'],
        // title: {
        //   placeholder: 'h1'
        // },

        // https://ckeditor.com/docs/ckeditor5/latest/api/module_core_editor_editorconfig-EditorConfig.html
        toolbar: {
          // items: ['Undo', 'Redo', 'selectAll', '|', 'heading', 'fontSize', 'bold', 'italic', 'strikethrough', 'underline', '|', 'alignment', 'numberedList', 'bulletedList', 'blockQuote', '|', 'link', 'uploadImage', 'MediaEmbed', 'insertTable', 'code'],
          shouldNotGroupWhenFull: true,
        },

        list: {
          properties: {
            styles: true,
            startIndex: true,
            reversed: true
          }
        },
        heading: {
          options: [
            { model: 'paragraph', title: 'Paragraph', class: 'ck-heading_paragraph' },
            { model: 'heading1', view: 'h1', title: 'Heading 1', class: 'ck-heading_heading1' },
            { model: 'heading2', view: 'h2', title: 'Heading 2', class: 'ck-heading_heading2' },
            { model: 'heading3', view: 'h3', title: 'Heading 3', class: 'ck-heading_heading3' },
            // { model: 'heading4', view: 'h4', title: 'Heading 4', class: 'ck-heading_heading4' },
            // { model: 'heading5', view: 'h5', title: 'Heading 5', class: 'ck-heading_heading5' },
            // { model: 'heading6', view: 'h6', title: 'Heading 6', class: 'ck-heading_heading6' }
          ]
        },
        placeholder: '',
        // 'codeBlock', 'htmlEmbed', 'sourceEditing'

        // toolbarGroups: [
        //   { name: 'document', groups: ['mode', 'document', 'doctools'] },
        // ],

        // easyimage: true,
        // easyimage_toolbar: ['EasyImageAlignLeft', 'EasyImageAlignCenter', 'EasyImageAlignRight'],

        // allowedContent: 'p b i; a[!href]',
        // on: {
        //   instanceReady: function (evt) {
        //     var editor = evt.editor;

        //     editor.filter.check('h1'); // -> false
        //     editor.setData('<h1><i>Foo</i></h1><p class="left"><span>Bar</span> <a href="http://foo.bar">foo</a></p>');
        //     // Editor contents will be:
        //     '<p><i>Foo</i></p><p>Bar <a href="http://foo.bar">foo</a></p>'
        //   }
        // }

        imageUploadConfig: {
          types: ['png', 'jpeg']
        }


      },
      editorInput: ``
    }
  },

  mounted() {
    console.log(this.editorConfig.ckbox.tokenUrl);
  }
}
</script>
<style lang="scss" scoped>
.ckeditor-preview {

  h1,
  h2,
  h3 {
    margin-bottom: 0;
    font-weight: bold;
  }

  h1 {
    font-size: 32px;
  }
}
</style>
