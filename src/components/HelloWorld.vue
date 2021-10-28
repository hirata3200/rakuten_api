<template>
  <div>
    <input class="form-control" type="text" v-model="input">
    <button class="btn btn-info mt-2" v-on:click="doAction">検索</button>
    <table>
      <tr>
        <td class="title">
          <h4>タイトル</h4><h2>{{ title }}</h2>
        </td>
        <!-- <td class="author">
          <h5>著者/イラスト</h5><h2>{{ author }}</h2>
        </td>
      </tr>
      <tr>
        <td class="itemcaption">
          <h4 style="text-align:center">あらすじ</h4><h3>{{ itemCaption }}</h3>
        </td>
        <td class="seriesnamekana">
          <h4>出版社</h4><h3>{{ seriesNameKana }}</h3>
        </td> -->
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      title: "",
      author: "",
      itemCaption: "",
      seriesNameKana: "",
    }
  },
  async methods: {
    doAction(){
    const url =
      "https://app.rakuten.co.jp/services/api/BooksBook/Search/20170404?format=json&title=%E3%82%BC%E3%83%AD%E3%81%8B%E3%82%89%E5%A7%8B%E3%82%81%E3%82%8B%E7%95%B0%E4%B8%96%E7%95%8C%E7%94%9F%E6%B4%BB%EF%BC%91&applicationId=1065554492451182173";
    const response = await fetch(url);
    const data = await response.json();
    this.title = data.Items[0].Item.title;
    // this.author = data.Items[0].Item.author;
    // this.itemCaption = data.Items[0].Item.itemCaption;
    // this.seriesNameKana = data.Items[0].Item.seriesNameKana;

    //v-onのページ見てやること
  },
};
</script>
<style>
.title {
  width: 250px;
  border: solid 5px blue;
  text-align: center;
  color: white;
  background-color: green;
}
.author {
  width: 130px;
  border: solid 5px red;
  text-align: center;
    color: white;
  background-color: green;

}
.itemcaption {
  width: 1000px;
  border: solid 2px red;
  text-align: left;
}
.seriesnamekana {
  width: 130px;
  border: solid 2px green;
  text-align: center;

}
</style>
