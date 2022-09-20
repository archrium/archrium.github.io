 <!-- Component Template 1.2 -->
   <!-- ----------------------------------------------------------------------
  --------- SCRIPTS
  ----------------------------------------------------------------------- -->
  <script>
    export default {
      name: "GotoTop",
      data() {
        return {
          prevScrollpos: 0,
          invertedColor: this.$colorMode.value
        };
      },
      computed: {
        invertedColorComputed() {
          return this.$colorMode.value == 'dark';
        }
      },
      created() {
        window.addEventListener("scroll", this.handleScroll);
      },
      unmounted() {
        window.removeEventListener("scroll", this.handleScroll);
      },
      methods: {
        handleScroll() {
          var currentScrollPos = window.pageYOffset;
          if (currentScrollPos < 100) {
            this.$refs['top'].style.bottom = "-5%";
          } else {
            this.$refs['top'].style.bottom = "10%";
          }
          this.prevScrollpos = currentScrollPos;
        },
        scrollToTop() {
          window.scrollTo(0, 0);
        },
      },
    };
    </script>
  
   <!-- ----------------------------------------------------------------------
  --------- TEMPLATE
  ----------------------------------------------------------------------- -->
  <template>
    <div :class="{'inverted-color': invertedColorComputed}" class="goto-top" ref="top" @click="scrollToTop">
      <img src="../assets/icons/arrow_left.png" alt="arrow" />
    </div>
  </template>   
  
  <!-- ----------------------------------------------------------------------
  --------- STYLE
  ----------------------------------------------------------------------- -->
  <!-- // ====  Style -->
  <style scoped>
  @media (max-width: 480px) {
    .goto-top {
      width: 100%;
      position: fixed;
      display: block;
      bottom: -5%;
      left: calc(var(--page-width-mobile)*.9);
      z-index: 10;
      transition: bottom 0.3s;
    }
  }
  
  @media (min-width: 481px) and (max-width: 1024px) {
    .goto-top {
      position: fixed;
      display: block;
      bottom: -5%;
      right: 10%;
      z-index: 10;
      transition: bottom 0.3s;
    }
  }
  
  @media (min-width: 1025px) {
    .goto-top {
      position: fixed;
      display: block;
      bottom: -5%;
      left: calc((var(--page-width)*1.5));
      z-index: 10;
      transition: bottom 0.3s;
    }
  }
    .goto-top:hover {
      cursor: pointer
    }
  
    .goto-top img {
      transform: rotate(90deg);
      max-width: 100%;
      max-height: 24px;
    }
  </style>
  