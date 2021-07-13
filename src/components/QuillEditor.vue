<template>
  <div>
    <quill-editor
      ref="myQuillEditor"
      v-model="content"
      :options="editorOption"
      :toolbar="[['bold', 'underline']]" 
      @blur="onEditorBlur($event)"
      @focus="onEditorFocus($event)"
      @ready="onEditorReady($event)"
    />
    <div class="text-center">
      <el-button
        :disabled="content.length === 0"
        type="primary"
        class="mt-1"
        size="small"
        plain
        @click="handleSave()"
        >Save
      </el-button>
    </div>
  </div>
</template>

<script>
import "quill/dist/quill.core.css";
import "quill/dist/quill.bubble.css";
export default {
  data() {
    return {
      content: "",
      editorOption: {
        theme:'snow',
        placeholder:"Текст заметки...",
        modules: {
        toolbar: [
          ['bold', 'italic', 'underline', 'strike'],
            
              [{ 'list': 'ordered' }, { 'list': 'bullet' }],
              [{ 'script': 'sub' }, { 'script': 'super' }],
              [{ 'indent': '-1' }, { 'indent': '+1' }],
              [{ 'size': ['small', false, 'large', 'huge'] }],
              [{ 'color': [] }, { 'background': [] }],
              [{ 'align': [] }],
        ],
      }

      },
    };
  },
  props: {
    text: String,
  },
  methods: {
    onEditorBlur(quill) {
      console.log("editor blur!", quill);
    },
    onEditorFocus(quill) {
      console.log("editor focus!", quill);
    },
    onEditorReady(quill) {
      console.log("editor ready!", quill);
    },
    onEditorChange({ quill, html, text }) {
      console.log("editor change!", quill, html, text);
      this.content = html;
    },
    handleSave() {
      console.log("save func :>> ");
      this.$emit("savePost", this.content);
      this.content = "";
    },
  },

  computed: {
    editor() {
      return this.$refs.myQuillEditor.quill;
    },
  },
  mounted() {
    console.log("this is current quill instance object", this.editor);
  },
};
</script>

<style scoped>
</style>
