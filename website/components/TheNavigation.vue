 <!-- Component Template 1.0 -->
 <!-- ----------------------------------------------------------------------
  --------- SCRIPTS
  ----------------------------------------------------------------------- -->
<script>
import json from "~/data/GuildStatus.json";

export default {
  name: 'TheNavigation',
  data() {
    return {
      json: json,
      prevScrollpos: 0,
    };
  },
  computed: {
    invertedColorComputed() {
      return this.$colorMode.value == 'dark';
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
    window.addEventListener("mousemove", this.handleMouseMove);
  },
  unmounted() {
    window.removeEventListener("scroll", this.handleScroll);
    window.removeEventListener("mousemove", this.handleMouseMove);
  },
  methods: {
    openResume() {
      const pdf = "../assets/pdf/kutay-coskuner_resume.pdf";
      window.open(pdf);
    },
    handleScroll() {
      var currentScrollPos = window.pageYOffset;
      if (currentScrollPos == 0) {
        this.$refs["navigation"].style.top = "0px";
      } else {
        this.$refs["navigation"].style.top = "calc(-1 * var(--navigation-height))";
      }
      this.prevScrollpos = currentScrollPos;
    },
    handleMouseMove(e) {
      if (e.clientY < 120) {
        this.$refs["navigation"].style.top = "0px";
      } else {
        var currentScrollPos = window.pageYOffset;
        if (currentScrollPos != 0)
          this.$refs["navigation"].style.top = "calc(-1 * var(--navigation-height))";
      }
    },
    scrollToTop() {
      window.scrollTo(0, 0);
    },
  },
}

</script>

 <!-- ----------------------------------------------------------------------
--------- TEMPLATES
----------------------------------------------------------------------- -->
<template>
  <div class="navigation-container" ref="navigation">
    <div class="navigation-general-wrapper">
      <div class="representation-wrapper">
        <div class="representation">
          <nuxt-link to="/">Archrium</nuxt-link>
        </div>
      </div>
      <!-- <div class="representation-mid-wrapper">
        <img src="~/assets/icons/discord.png" alt="">
      </div> -->
      <div class="navigation-menu-wrapper">
        <div class="navigation-menu">
          <nuxt-link to="/guild">Guild</nuxt-link>
          <nuxt-link to="/guides">Guides</nuxt-link>
          <nuxt-link to="/strategy">Strategy</nuxt-link>
          <div class="navigation-icons">
            <a :class="{'inverted-color': invertedColorComputed}" :href="json.links.discord"><img src="~/assets/icons/discord.png"
                alt="dsc"></a>
            <a :class="{'inverted-color': invertedColorComputed}" :href="json.links.github"><img src="~/assets/icons/github.png"
                alt="dsc"></a>
            <ColorMode />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  <!-- ----------------------------------------------------------------------
  --------- STYLES
  ----------------------------------------------------------------------- -->
<style scoped>
@media (max-width: 480px) {
  .navigation-general-wrapper {
    width: var(--page-width-mobile);
    margin: auto;
  }

  .representation-wrapper {
    width: 100%;
    min-height: var(--navigation-height-mobile);
    text-align: center;
    text-transform: uppercase;
  }

  .navigation-menu-wrapper {
    width: 100%;
    min-height: var(--navigation-height-mobile);
    display: flex;
    align-items: center;
    justify-content: center;
    /*  */
  }

  .navigation-menu {
    width: 100%;
    display: flex;
    padding-top: 2%;
    justify-content: center;
  }

  .navigation-menu * {
    color: var(--color);
    text-decoration: none;
    text-transform: uppercase;
    font-size: 80%;
    font-weight: 400;
    border-bottom: 0px solid var(--color-border);
    margin: auto;
    opacity: 80%;
  }
}

@media (min-width: 481px) and (max-width: 1024px) {
  .navigation-general-wrapper {
    width: var(--page-width-mobile);
    margin: auto;
  }

  .representation-wrapper {
    /* width: 40%; */
    min-height: var(--navigation-height-tablet);
    /*  */
    position: relative;
    float: left;
    /*  */
    display: flex;
    align-items: center;
    /* justify-content: center; */
    /*  */
    text-align: center;
    text-transform: uppercase;
    /* border: 1px solid #ccc; */
  }

  .navigation-menu-wrapper {
    /* width: 40%; */
    min-height: var(--navigation-height-tablet);
    /*  */
    position: relative;
    float: right;
    /*  */
    display: flex;
    align-items: center;
    justify-content: center;
    /*  */
  }

  .navigation-menu {
    width: 100%;
    display: flex;
    padding-top: 2%;
    justify-content: right;
  }

  .navigation-menu * {
    color: var(--color);
    text-decoration: none;
    text-transform: uppercase;
    font-size: 80%;
    font-weight: 400;
    border-bottom: 0px solid var(--color-border);
    margin: 0 0 0 3em;
    opacity: 80%;
  }
}

@media (min-width: 1025px) {
  .navigation-general-wrapper {
    width: var(--page-width);
    margin: auto;
  }

  .representation-wrapper {
    /* width: 40%; */
    min-height: var(--navigation-height);
    /*  */
    position: relative;
    float: left;
    /*  */
    display: flex;
    align-items: center;
    /* justify-content: center; */
    /*  */
    text-align: center;
    text-transform: uppercase;
    /* border: 1px solid #ccc; */
  }

  .navigation-menu-wrapper {
    /* width: 40%; */
    min-height: var(--navigation-height);
    /*  */
    position: relative;
    float: right;
    /*  */
    display: flex;
    align-items: center;
    justify-content: center;
    /*  */
  }

  .navigation-menu {
    width: 100%;
    display: flex;
    padding-top: 2%;
    justify-content: right;
  }

  .navigation-menu * {
    color: var(--color);
    text-decoration: none;
    text-transform: uppercase;
    font-size: 80%;
    font-weight: 400;
    border-bottom: 0px solid var(--color-border);
    margin: 0 0 0 4em;
    opacity: 80%;
  }
}

/* <!-- ==== General */
.navigation-container {
  background: var(--bg-transparent);
  color: var(--color);
  backdrop-filter: var(--main-blur);
  /*  */
  width: 100%;
  /*  */
  margin: auto;
  position: fixed;
  display: block;
  transition: top 0.2s;
  /*  */
  z-index: 10;
}


.representation a {
  color: var(--color);
  font-size: 150%;
  letter-spacing: .1em;
  opacity: 80%;
  text-decoration: none;

}

.representation a:hover {
  opacity: 90%;
  transition: opacity, 0.3s;
  cursor: pointer;
}

.representation-mid-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40%;
}

.representation-mid-wrapper img {
  display: block;
  margin: auto;
  width: 30%;
}

.navigation-menu a:hover {
  transition: border-bottom 0.3s;
  border-bottom: 1px solid var(--color-border);
}

.navigation-menu a:active {
  color: var(--color-primary);
}

.navigation-icons {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: calc(2 * var(--main-font-size));
  position: relative;
  bottom: calc(-.2 * var(--main-font-size));
}

.navigation-icons * {
  width: 120%;
  height: 100%;
  margin: 0;
  padding: 0;
}

.navigation-icons a:hover {
  border-bottom: 0px solid var(--bg);
}

.navigation-icons *:hover {
  filter: drop-shadow(0 0 .4em var(--icon-glow));
}

.navigation-icons img {
  object-fit: contain;

  width: calc(2 * var(--main-font-size));
  height: calc(2 * var(--main-font-size));
  filter: grayscale(1);
  /* filter: invert(1); */
}

.noselect {
  -webkit-touch-callout: none;
  /* iOS Safari */
  -webkit-user-select: none;
  /* Safari */
  -khtml-user-select: none;
  /* Konqueror HTML */
  -moz-user-select: none;
  /* Old versions of Firefox */
  -ms-user-select: none;
  /* Internet Explorer/Edge */
  user-select: none;
}
</style>
  