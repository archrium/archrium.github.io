<!-- ----------------------------------------------------------------------
--------- TEMPLATE
---------------------------------------------------------------------------
 -->
<template>
    <div class="website-container">
        <!-- ==== Accessibility -->
        <TheNavigation />
        <GotoTop />
        <!-- ==== Content -->
        <div class="content-container">
            <div class="content">
                <Nuxt />
            </div>
        </div>
        <!-- ==== Footer -->
        <!-- ==== Overlay -->
        <!-- <ImageSlider /> -->
    </div>
</template>

<!-- ----------------------------------------------------------------------
--------- SCRIPTS
---------------------------------------------------------------------------
 -->
<script>

</script>
  
<!-- ----------------------------------------------------------------------
--------- STYLE
---------------------------------------------------------------------------
 -->
<style>
@media (max-width: 480px) {
    .content-container {
    height: calc(100%);
    width: var(--page-width-mobile);
    margin: var(--navigation-height-mobile) auto auto auto;
}
}

@media (min-width: 481px) and (max-width: 1024px) {
    .content-container {
    height: calc(100%);
    width: var(--page-width-tablet);
    margin: var(--navigation-height-tablet) auto auto auto;
}
}

@media (min-width: 1025px) {
    .content-container {
    height: calc(100%);
    width: var(--page-width);
    margin: var(--navigation-height) auto auto auto;
}
}
html,
body,
#__nuxt,
#__layout {
    scroll-behavior: smooth;
    /* background-color: var(--bg-color); */
    /* color: var(--fg-color); */
    height: 100% !important;
    width: 100% !important;
    max-width: 1920px !important;
    margin: auto;
    padding: 0;
    font-weight: normal;
    font-style: normal;
    font-size: var(--main-font-size);
    /* overflow-y: hidden !important; */
}

h1, h2, h3, h4, h5, h6, p {
    margin: 0;
}

body.no-scroll {
    overflow-y: hidden !important;
}

.null-link {
    color: #ccc !important;
}

/* ==== Structure */
/* == Website Container */
.website-container {
    display: flex;
    flex-flow: column;
    width: 100%;
    height: 100%;
}

/* == Content */
.content {
    height: 100%;
    width: 100%;
    /* border: 1px solid #ccc */
}

.content img {
    max-height: 100%;
    max-width: 100%;
}
</style>