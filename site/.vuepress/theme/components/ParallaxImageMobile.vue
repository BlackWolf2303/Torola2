<template>
  <div v-if="$mq==='mobile'|$mq==='tablet'" id="parallax-image-mobile" class="container">
    <!-- Portfolio Item -->
    <figure class="parallax-folio-item-mobile">
      <div class="item-media" :style="changeImagePosition">
        <img v-parallax="-0.1" :src="src" :alt="alt">
      </div>
      <figcaption  id="figcaption" class="visible" :data-aos="AosValue" :style="changeFigcaptionPosition">
        <div class="item-caption-inner-mobile">
          <p class="text-links">
            <a href="#">Design</a>
            <a href="#">Art</a>
          </p>
          <h3 class="bold uppercase">{{title}}</h3>
          <a href="#" class="button style-3 border-2">View Project</a>
        </div>
      </figcaption>
    </figure>
    <!-- /Portfolio Item -->
  </div>
 <!-- figcaption under 768px (325,170) -->

</template>

<script>
import Vue from "vue";
import VueParallaxJs from "vue-parallax-js";
import AOS from 'aos';
import "aos/dist/aos.css";
import VueMq from 'vue-mq';

Vue.use(VueMq, {
  breakpoints: {
    mobile: 450,
    tablet: 768,
    laptop: 1024,
    desktop: Infinity,
  }
});
Vue.use(VueParallaxJs);
Vue.use(AOS);

export default {
  name: "ParallaxImageMobile",
  props: ["title", "src", "alt", "left", "right","aosValue"],

  created(){
    AOS.init();
  },
  data () {
  return {
    AosValue: this.aosValue,
  }
  },
  computed: {
    changeFigcaptionPosition() {
      return "left:" + this.left;
      
      
    },
    changeImagePosition() {
      return "margin-left:" + this.right;
    },
  
    
  },
  mounted: 
    function() { 
    setTimeout(function() {
      window.scrollTo(0, 5);
      window.scrollTo(0, 0);
    }, 100);
  },
};

</script>

<style lang="scss" scoped>

#parallax-image-mobile {
  @media (max-width: 767.98px){
    max-width: 720px;
  }

  .parallax-folio-item-mobile {
    // height: 450px;
    max-width: 1140px;
    margin: 0 auto;
    margin-bottom: 150px;
    position: relative;
    overflow: hidden;
    width: 100%;
    font-size: 1.4rem;
    font-weight: 400;
    letter-spacing: 0.05em;
    line-height: 1.5;
    color: #222;
      .item-media {
      position: relative;
      width: 70%;
      @media (max-width: 767.98px) {
      margin: auto;
      width: 100%;
      }

    }
  }
  figure {
    margin: 0;
    display: block;
  }
  .item-media {
    max-height: 325px;
    overflow: hidden;
    margin-left: auto;
    margin-right: auto;
    @media (max-width: 767.98px) {
      max-width: 540px;
    }
    @media (max-width: 424.98px) {
      max-width: 100%;
      max-height: 240px;
    }
    img {
      @media (max-width: 767.98px) {
      max-width: 540px;
      }
      @media (max-width: 424.98px) {
      max-width: 400px;
    }
    }
  }
  .parallax-folio-item-mobile figcaption {
    display: block;
    background-color: #fff;
    @media (max-width: 767.98px){
      max-width: 78%;
      max-height: 170px;
      margin: auto;
    }
    @media (max-width: 424.98px){
      max-width: 100%;
      max-height: 170px;
      margin: auto;
    }
  }
  .visible {
    visibility: visible !important;
  }
  .parallax-folio-item-mobile figcaption.visible .item-caption-inner-mobile {
    opacity: 1;
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
  }
  .parallax-folio-item-mobile .item-caption-inner-mobile {
    position: relative;
    padding: 30px 40px 20px;
    opacity: 0;
    -webkit-transform: translate3d(70px, 0, 0);
    transform: translate3d(70px, 0, 0);
    -webkit-transition: all 1s ease;
    transition: all 1s ease;
    -webkit-transition-delay: 0.3s;
    transition-delay: 0.3s;
    font-family: sans-serif;
    font-weight: 700;
    box-shadow: 0 10px 50px 0 rgba(0, 0, 0, 0.1),
      0 6px 10px 0 rgba(0, 0, 0, 0.1);

    h3 {
      font-size: 3.7897rem;
      line-height: 1;
      margin: 0 0 0.45em -0.04em;
      text-transform: uppercase;
      @media (max-width: 767.98px){
        font-size: 2.6rem;
    }
    }
  }
  .parallax-folio-item-mobile figcaption .text-links {
    font-size: 13px;
    font-style: italic;
    font-family: "Playfair Display", serif;
    p {
      margin: 0 0 0.6em;
      color: #757575;
    }
  }
  .parallax-folio-item-mobile figcaption .text-links a {
    color: #757575;
  }
  .text-links a {
    position: relative;
    text-decoration: none;
    color: inherit;
    background-color: transparent;
  }

  .text-links a:not(:first-child):before {
    content: "/";
    position: absolute;
    width: 1.3em;
    right: 100%;
    text-align: right;
    color: rgba(0, 0, 0, 0.6);
  }
  .text-links:after {
    content: "";
    height: 1px;
    width: 100%;
    background-color: currentColor;
    position: absolute;
    bottom: 0;
    left: 0;
    -webkit-transform: scaleX(0);
    transform: scaleX(0);
    -webkit-transform-origin: right;
    transform-origin: right;
    -webkit-transition: -webkit-transform 0.3s ease;
    transition: -webkit-transform 0.3s ease;
    transition: transform 0.3s ease;
    transition: transform 0.3s ease, -webkit-transform 0.3s ease;
  }
  .button.border-2 {
    border-width: 4px;
    line-height: 37px;
  }
  .button.style-3 {
    background-color: transparent;
    border-color: #dedede;
    color: #000;
  }
  .button {
    display: inline-block;
    position: relative;
    font-family: inherit;
    text-decoration: none !important;
    vertical-align: middle;
    white-space: nowrap;
    text-overflow: ellipsis;
    text-align: center;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    border-radius: 0;
    letter-spacing: 0.04em;
    cursor: pointer;
    z-index: 1;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    outline: 0 !important;
    -webkit-transition: all 0.2s ease;
    transition: all 0.2s ease;
    font-size: 1.2rem;
    font-weight: 700;
    text-transform: uppercase;
    padding: 0 2.2em;
    height: 44px;
    line-height: 41px;
    margin-bottom: 20px;
    background-color: #333;
    color: #fff;
    border: 2px solid transparent;
  }
  .button.style-3:hover {
    border-color: #000;
  }

}
</style>