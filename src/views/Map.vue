<template>
  <div class="container">
    <br />
    <br />
    <br />
    <h1>Titulo</h1>
    <p>Descrição</p>
    <hr />
    <div class="container col-sm-12">
      <h2>Comentários</h2>
      <form v-on:submit.prevent="addComment()" v-if="this.$store.state.loggedUser.length != 0">
        <div class="form-group">
          <textarea
            class="form-group"
            style="resize: none"
            id="comment"
            rows="2"
            v-model="textComment"
          ></textarea>
        </div>
        <button type="submit">Comentar</button>
        <br>
        <br>
        
      </form>

      <div class="slidecontainer">
          <b id="change">1</b><input type="range" min="1" max="5" value="0" class="slider" id="myRange" v-model="rating" />5
          <p >
            Value:{{rating}}
            <span id="demo"></span> <br>
            <button id="btnPoints">Pontuar</button>
          </p>
        </div>
      <div v-for="comment in this.$store.state.comments.slice().reverse()" v-bind:key="comment">
        <!-- <span v-if='idWinerie == this.$store.state.winerieSelected'></span> -->
        <hr />
        <h5>{{comment.name}}</h5>
        <div class="row">
          <p class="col-sm-10">{{comment.comment}}</p>
          <button>APAGAR</button>
        </div>
        <small>{{comment.date}} {{comment.hour}}</small>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data: () => ({
    textComment: "",
    typeUser: "",
    rating:"",
  }),
  created: function() {
    window.addEventListener("unload", this.saveStorage);
    if (localStorage.getItem("comments")) {
      this.$store.state.comments = JSON.parse(localStorage.getItem("comments"));
    }
  },
  computed: {
    getTypeUser() {
      return this.$store.getters.typeUser;
    }
  },
  methods: {
    getLastId() {
      return this.$store.getters.lastIdComment;
    },
    addComment() {
      let today = new Date();
      let day = today.getDate();
      let month = today.getMonth() + 1;
      let year = today.getFullYear();
      let hour = today.getHours();
      let minutes = today.getMinutes();
      alert();
      this.$store.commit("ADD_COMMENT", {
        idComment: this.getLastId() + 1,
        idWinerieComment: 1,
        emailComment: this.$store.getters.email,
        nameComment: this.$store.getters.name,
        textComment: this.textComment,
        dateComment: `${day}/${month}/${year}`,
        hourComment: `${hour}:${minutes}`
      });
      this.textComment = "";
    }
  }
};
</script>
<style>
.slidecontainer {
  width: 100%;
}

.slider {
  -webkit-appearance: none;
  width: 20%;
  height: 10px;
  border-radius: 8px;
  background: #c051c0;
  outline: 5px;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider:hover {
  opacity: 1;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 23px;
  height: 24px;
  border: 0;
  background: url(
    "../assets/circuloverde1.png"
  );
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 20px;
  height: 21px;
  border: 0;
  background: url('../assets/circuloverde1.png');
  cursor: pointer;
}


</style>