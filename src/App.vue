<script setup>
import Data from "./assets/data";
import DataBarang from "./assets/dataBarang";
</script>
<script>
export default {
  data: function () {
    return {
      content: Data,
      popUp: false,
      birthDay: "",
      openedTab1: true,
      openedTab2: false,
      titleHero: "Centered Hero",
      titleImage:
        "https://media.istockphoto.com/photos/koala-picture-id537179382?k=20&m=537179382&s=612x612&w=0&h=t_uwjhdeiH70yO-GOl7iLngz2gzBxdGkW0d1LBqxlJI=",
    };
  },
  methods: {
    changeTitle(data) {
      this.titleHero = data.nama;
      this.titleImage = data.image;
      this.popUp = true;
    },
    closePopUp() {
      this.popUp = false;
    },
    showDate(value) {
      // alert(value);
      this.birthDay = value;
    },
    openTab1() {
      this.openedTab1 = true;
      this.openedTab2 = false;
    },
    openTab2() {
      this.openedTab2 = true;
      this.openedTab1 = false;
    },
  },
};
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
      <a class="navbar-brand" href="">Navbar {{ birthDay }}</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarTogglerDemo02"
        aria-controls="navbarTogglerDemo02"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="">Contact</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="">Pricing</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="">Download</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <div>
    <div class="scrollmenu">
      <a href="#home">Home</a>
      <a href="#news">News</a>
      <a href="#contact">Contact</a>
      <a href="#about">About</a>
      <a href="#support">Support</a>
      <a href="#blog">Blog</a>
      <a href="#tools">Tools</a>
      <a href="#base">Base</a>
      <a href="#custom">Custom</a>
      <a href="#more">More</a>
      <a href="#logo">Logo</a>
      <a href="#friends">Friends</a>
      <a href="#partners">Partners</a>
      <a href="#people">People</a>
      <a href="#work">Work</a>
    </div>
  </div>
  <div class="container">
    <div class="tab" @click="openTab1">tab1</div>
    <div class="tab" @click="openTab2">tab2</div>
    <div class="isitab-1" v-bind:class="openedTab1 && 'show'">
      orem Ipsum is simply dummy text of the printing and typesetting industry.
      Lorem Ipsum has been the industry's standard dummy text ever since the
      1500s, when an unknown printer took a galley of type and scrambled it to
      make a type specimen book. It has survived not only five centuries, but
      also the leap into electronic typesetting, remaining essentially
      unchanged. It was popularised in the 1960s with the release of Letraset
      sheets containing Lorem Ipsum passages, and more recently with desktop
      publishing software like Aldus PageMaker including versions of Lorem
      Ipsum.
    </div>
    <div class="isitab-2" v-bind:class="openedTab2 && 'show'">
      There are many variations of passages of Lorem Ipsum available, but the
      majority have suffered alteration in some form, by injected humour, or
      randomised words which don't look even slightly believable. If you are
      going to use a passage of Lorem Ipsum, you need to be sure there isn't
      anything embarrassing hidden in the middle of text. All the Lorem Ipsum
      generators on the Internet tend to repeat predefined chunks as necessary
    </div>
  </div>

  <div class="">
    <div v-for="data in Data" style="display: inline-block; max-width: 100px">
      <img :src="data.image" alt="..." style="width: 100%" />
    </div>
  </div>
  <div class="container">
    <div class="px-4 py-5 my-5 text-center">
      <img
        class="d-block mx-auto mb-4"
        :src="titleImage"
        alt=""
        width="720"
        height="570"
      />
      <svg class="bi" width="32" height="32" fill="white">
        <use xlink:href="bootstrap-icons.svg#heart-fill" />
      </svg>
      <h1 class="display-5 fw-bold">{{ titleHero }}</h1>
      <div class="col-lg-6 mx-auto">
        <p class="lead mb-4">
          Quickly design and customize responsive mobile-first sites with
          Bootstrap, the world’s most popular front-end open source toolkit,
          featuring Sass variables and mixins, responsive grid system, extensive
          prebuilt components, and powerful JavaScript plugins.
        </p>
        <div class="d-grid gap-2 d-sm-flex justify-content-sm-center">
          <button type="button" class="btn btn-primary btn-lg px-4 gap-3">
            Primary button
          </button>
          <button type="button" class="btn btn-outline-secondary btn-lg px-4">
            Secondary
          </button>
        </div>
      </div>
    </div>
  </div>
  <div>
    <div class="input-group">
      <input type="date" id="birthday" name="birthday" v-model="value" />
      <button @click="showDate(value)">add date</button>
    </div>
  </div>
  <div class="outsideContainer" v-bind:class="popUp && 'shown'">
    <div class="containerModal">
      <div>
        <div class="closeButton" @click="closePopUp">x</div>
        <div class="row text-center">
          <h1 class="display-5 fw-bold">{{ titleHero }}</h1>
          <img
            class="d-block mx-auto mb-4"
            :src="titleImage"
            alt=""
            width="720"
            height="570"
          />
        </div>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="row">
      <div class="col mt-5" v-for="data in DataBarang">
        <div class="card" style="width: 18rem">
          <img :src="data.image" class="card-img-top" alt="..." />
          <div class="card-body text-center">
            <h5 class="card-title title-name">{{ data.nama }}</h5>
            <p class="card-text subtitle-name">
              Some quick example text to build on the card title and make up the
              bulk of the card's content.
            </p>
            <button @click="changeTitle(data)" href="#" class="btn btn-primary">
              Go somewheres
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}
div.scrollmenu {
  background-color: #333;
  overflow: auto;
  white-space: nowrap;
}

div.scrollmenu a {
  display: inline-block;
  color: white;
  text-align: center;
  padding: 14px;
  text-decoration: none;
}

div.scrollmenu a:hover {
  background-color: #777;
}
.title-name {
  color: black;
  text-transform: capitalize;
}
.subtitle-name {
  color: grey;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
}
.closeButton {
  font-size: 50px;
  font-weight: bold;
  top: -40px;
  position: absolute;
  right: 0;
  cursor: pointer;
  z-index: 10;
}
.tab {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}
.tab:hover {
  background-color: white;
  color: hotpink;
}
.isitab-1 {
  background-color: grey;
  visibility: hidden;
  height: 0;
}
.isitab-2 {
  background-color: grey;
  visibility: hidden;
  height: 0;
}
.isitab-1.show {
  visibility: visible;
}
.isitab-2.show {
  visibility: visible;
}
.outsideContainer {
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.8);
  visibility: hidden;
  opacity: 0;
  transition-property: all;
  transition-duration: 1s;
  z-index: 10;
}
.containerModal {
  background-color: white;
  padding: 20px;
  color: black;

  width: 100%;
  z-index: 10;
  width: 400px;
  height: 400px;
  margin: 40vh auto;
}
.containerModal img {
  height: 300px;
}
.outsideContainer.shown {
  visibility: visible;
  opacity: 1;
}
@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
