<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3" >
      <form id="transForm" class="jumbotron form-inline"  v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="zh">中文</option>
          <option value="ja">Japanese</option>
          <option value="ko">Korean</option> 
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "translateForm",
  data: function() {
    return {
      textToTranslate: "",
      language: ""
    };
  },
  methods: {
    formSubmit: function(e) {
      //alert(this.textToTranslate)
      this.$emit("formSubmit", this.textToTranslate, this.language);
      e.preventDefault();
    }
  },
  created: function() {
    this.language = "en";
  }
};
</script>

<style scoped>
#transForm {
  border: 1px solid #ccc;
  border-radius: 10px;
}
#transForm select,
#transForm input {
  margin-bottom: 6px;
}
</style>
