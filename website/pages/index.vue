<template>
  <div class="main">
    <div>
      <h2>Welcome to Archrium</h2>
      <br>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed varius laoreet ipsum nec gravida.
        <br><br>
        Phasellus id tellus id velit suscipit hendrerit non vel nunc. Pellentesque tempus lectus ipsum, et
        euismod nunc convallis eget. Nam non ante sit amet mauris volutpat auctor. Aenean faucibus quam non
        efficitur pellentesque. Ut vitae dui a tortor posuere convallis quis in odio. Maecenas accumsan arcu
        augue, molestie vehicula nibh accumsan nec. Morbi sit amet urna a velit cursus consequat. Nulla porta
        semper ante varius feugiat.
        <br><br>
        Nunc sed venenatis dui, a pharetra erat. Nulla eros sem, hendrerit vitae tristique eget, aliquet vitae
        risus. Sed sit amet ligula sed ipsum sagittis pharetra. Nullam in odio sed lectus lacinia lobortis vitae
        molestie lacus. Donec efficitur elit odio, non pellentesque nisl pharetra condimentum. Maecenas ut orci
        libero. Curabitur non nisi imperdiet.
      </p>
      <br />
      <hr>
      <br />
      <div class="guild-status">
        <h2>Guild Status</h2>
        <br />
        <h4 class="guild-update"><i> Last Update: {{ json.update }} </i></h4>
        <br />
        <span style="text-transform:capitalize" v-for="(state, index) in json.states">
          <span v-if="state.state == true" style="font-weight:bold" :style="{'color':state.color}">
            {{ state.name }}
          </span>
          <span v-else style="color:var(--color);opacity:.5;">
            {{ state.name }}
          </span>
          <span style="color:var(--color);opacity:.4;" v-if="index + 1 < json.states.length"> | </span>
        </span>
      </div>
    </div>
    <div class="image">
      <img src="../assets/img/artwork_wotlk-gear.png" alt="artwork">
    </div>
  </div>
</template>

<script>
import json from "../data/GuildStatus.json";

export default {
  name: 'IndexPage',
  layout: 'default',
  data() {
    return {
      json: json,
    };
  },
}
</script>

<style scoped>
@media (max-width: 480px) {
  .main {
    display: grid;
    margin: 0;
    padding-top: calc(1.5 * var(--navigation-height-mobile));

  }

  .image {
    position: fixed;
    opacity: .2;
  }
}

@media (min-width: 481px) and (max-width: 1024px) {
  .main {
    display: grid;
    margin: 0;
    padding-top: calc(1.5 * var(--navigation-height-mobile));

  }

  .image {
    position: fixed;
    opacity: .2;
  }
}

@media (min-width: 1025px) {
  .main {
    display: grid;
    grid-template:
      "a a"
      "a a"
      "c c";
    margin: 0;
    padding-top: calc(var(--navigation-height));
  }
}

.main {
  text-align: justify;
  text-justify: inter-word;
}

.main img {
  object-fit: cover;
  height: 100%;
  width: 100%;
  filter: grayscale(.8);
  opacity: .6;
}

.main h1 {
  margin: 0;
}

.guild-status {
  text-align: center;
  margin: auto;
}

.guild-update {
  color: var(--color-primary);
}
</style>

