<template>
  <div>
    <img class="img-top" src="../assets/MainPagePicture.jpg" />
    <div class="divider"></div>
  </div>
  <div class="main">
    <div class="head-container">
      <h3 class="head-text-container">
        Blivande front-end utvecklare med stort intresse för back-end utveckling
        <p>
          Hej och välkommen till min portfolio! <br />
          Mitt namn är william ali, 29 årig utvecklare från sverige.
        </p>
        <p>
          Här kommer ni hitta information om mig och projekten jag har jobbat
          med och även projekt jag aktuellt jobbar på!
        </p>
        <router-link to="/projects">Klicka här för att direkt komma till mina projekt!</router-link>
      </h3>
      <div class="empty">
      </div>

      <Carousel @next="next" @prev="prev" @stop="stop" @resume="resume" class="carousel" :projectTitle="projectTitle">
        <Carousel-slide v-for="(slide, index) in slides" :key="slide" :index="index" :visableSlide="visableSlide"
          :direction="direction">
          <router-link :to="'project/' + slide.id"><img class="image-scale" :src="slide.img" alt="" /></router-link>
        </Carousel-slide>
      </Carousel>

    </div>
  </div>
  <div class="divider"></div>

  <div class="mid-container">
    <div>
      <h1>Språk</h1>
      <div class="content-align">
        <img src="../assets/icons/icons8-html-5-32.png" width="32" height="32" alt="HTML5 Powered"
          title="HTML5 Powered" />
        <h3>Html</h3>
      </div>
      <div class="content-align">
        <img src="../assets/icons/icons8-css3-32.png" width="32" height="32" />
        <h3>Css</h3>
      </div>
      <div class="content-align">
        <img src="../assets/icons/icons8-javascript-32.png" width="32" height="32" />
        <h3>Js</h3>
      </div>
      <div class="content-align">
        <img src="../assets/icons/icons8-c-sharp-logo-32.png" width="32" height="32" />
        <h3>C#</h3>
      </div>
    </div>
    <div>
      <h1>Frameworks</h1>
      <div class="content-align">
        <img src="../assets/icons/icons8-.net-framework-32.png" width="32" height="32" />
        <h3>ASP.NET</h3>
      </div>
      <div class="content-align">
        <img src="../assets/icons/icons8-.net-framework-32.png" width="32" height="32" />
        <h3>Entity framework</h3>
      </div>
      <div class="content-align">
        <img src="../assets/logo.png" width="32" height="32" />
        <h3>Vue.js</h3>
      </div>
    </div>
    <div>
      <h1>Databaser</h1>
      <div class="content-align">
        <img src="../assets/icons/icons8-sql-32.png" width="32" height="32" />
        <h3>SQL</h3>
      </div>
      <div class="content-align">
        <img src="../assets/icons/icons8-mongodb-32.png" width="32" height="32" />
        <h3>MongoDb</h3>
      </div>
    </div>
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import CarouselSlide from "@/components/CarouselSlide.vue";
export default {
  components: {
    Carousel,
    CarouselSlide,
  },
  data() {
    return {
      slides: [
        {
          id: 0,
          imageName: "Att göra app",
          img: require("@/assets/testTodo.png"),
        },
        {
          id: 1,
          imageName: "Blogg app",
          img: require("@/assets/Blogg/SizeTest.png"),
        },
        {
          id: 2,
          imageName: "Brödernas Clone",
          img: require("@/assets/BrödernasClone/Home.png"),
        },
        {
          id: 3,
          imageName: "WebShop",
          img: require("@/assets/Webshop/Home.png"),
        },
      ],
      visableSlide: 0,
      index: 0,
      direction: "left",
      interval: null,
      projectTitle: "",
    };
  },
  computed: {
    slidesLen() {
      return this.slides.length;
    },
  },
  methods: {
    next() {
      if (this.visableSlide >= this.slidesLen - 1) {
        this.visableSlide = 0;
        this.projectTitle = this.slides[this.visableSlide].imageName;
      } else {
        this.visableSlide++;
        this.projectTitle = this.slides[this.visableSlide].imageName;
      }
      this.direction = "left";
    },
    prev() {
      if (this.visableSlide <= 0) {
        this.visableSlide = this.slidesLen - 1;
        this.projectTitle = this.slides[this.visableSlide].imageName;
      } else {
        this.visableSlide--;
        this.projectTitle = this.slides[this.visableSlide].imageName;
      }
      this.direction = "right";
    },
    stop() {
      clearInterval(this.interval);
    },
    resume() {
      this.interval = setInterval(() => {
        this.next();
      }, 3000);
    },
  },
  created() {
    this.projectTitle = this.slides[this.index].imageName;
    this.interval = setInterval(() => {
      this.next();
    }, 3000);
  },
  unmounted() {
    clearInterval(this.interval);
  },
};
</script>

<style scoped>
p
{
  font-size: 14.5px;
}

h3
{
  font-size: 25px;
}

.main
{
  margin-top: 5em;
}

.image-scale
{
  width: 700px;
  height: 400px;
  object-fit: cover;
}

.head-container
{
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 0.3fr 0.3fr;
  grid-template-areas: "headtext carousel"
    "empty btn-container";
  gap: 200px;
  row-gap: 0;
}

.carousel
{
  margin-left: 50px;
  grid-area: carousel;
}

.heading-text
{
  grid-area: headingText;
}

.empty
{
  grid-area: empty;
}

.head-text-container
{
  grid-area: headtext;
  width: 150%;
  margin-top: 100px;
}

.head-text-container p
{
  width: 80%;
  margin: 10px 0px;
}

.head-text-container a
{
  font-size: 14px;
  padding-left: 5px;
  color: rgb(155, 106, 106);
}

.head-text-container a:hover
{
  color: var(--clr-hover-link);
}

.img-top
{
  margin-top: 5px;
  width: 100%;
  height: 450px;
  margin-top: 20px;
  margin-bottom: 5px;
  border-radius: 10px;
  box-shadow: 1px 2px black;
  object-fit: cover;
}

.divider
{
  margin-top: 50px;
  background: black;
  width: 100%;
  height: 20%;
  border: 1px solid black;
}

.mid-container
{
  display: flex;
  flex-wrap: wrap;
  column-fill: balance;
  width: 100%;
  margin-bottom: 20px;
  margin-top: 20px;
  column-gap: 394px;
  row-gap: 5px;
}

.mid-container h1
{
  text-decoration: underline;
}

.content-align
{
  display: flex;
  gap: 10px;
  align-items: center;
}

@media screen and (max-width:4000px) and (min-width: 2880px)
{
  p
  {
    font-size: 30px;
  }

  h3
  {
    font-size: 50px;
  }

  .head-text-container a
  {
    font-size: 30px;
  }

  .main
  {
    margin: 60px 0px;
  }

  .head-container
  {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 0.3fr 0.3fr;
    grid-template-areas: "headtext carousel"
      "empty btn-container";
    gap: 500px;
    row-gap: 0;
  }

  .head-text-container
  {
    grid-area: headtext;
    width: 100%;
    margin-top: 15px;
    font-size: 11ch;
  }

  .mid-container
  {
    display: flex;
    width: 100%;
    margin-bottom: 20px;
    margin-top: 20px;
    gap: 850px;
    font-size: 6ch;
  }

  .content-align
  {
    display: flex;
    gap: 5px;
    align-items: center;

  }
}

@media screen and (max-width:768px) and (min-width: 480px)
{
  .main
  {
    margin: 0;
  }

  .head-container
  {
    display: flex;
    flex-direction: column;
  }

  .head-text-container
  {
    grid-area: headtext;
    width: 100%;
    margin-top: 15px;
  }

  .mid-container
  {
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    margin-bottom: 20px;
    margin-top: 20px;
    column-gap: 150px;
    row-gap: 5px;
  }

  .content-align
  {
    display: flex;
    gap: 5px;
    align-items: center;
  }
}

@media (max-width: 425px)
{

  .main
  {
    margin-top: 0em;
  }

  .head-container
  {
    display: flex;
    width: 100%;
    flex-direction: column;
    row-gap: 0;
  }

  .head-text-container
  {
    grid-area: headtext;
    width: 100%;
  }

  .mid-container
  {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    margin-bottom: 20px;
    margin-top: 20px;
    column-gap: 150px;
    row-gap: 30px;
  }

  .content-align
  {
    display: flex;
    gap: 5px;
    align-items: center;
  }
}
</style>