<script setup>

const page = ref(1);
const lang = ref(0)
const lightmode = ref(true)

const changeMode = () => {
  lightmode.value = !lightmode.value;
}

const updatePage = (pg) => {
  page.value = parseInt(pg);
}

const switchLang = () => {
  lang.value = (lang.value + 1) % 2;
  console.log(lang.value);
}

</script>

<template>
  <div :class= " !lightmode ? 'dark' : '' " class="">
    <div class="dark:bg-slate-800">
      <div class=" max-w-7xl mx-auto h-screen px-10 ">
        <Navbar 
            @changeMode="changeMode" 
            @update="updatePage" 
            @switch="switchLang" 
            :lightmode="lightmode" 
            :lang="lang "
            :active="page"
          />
        <Info v-if="page === 1" />
        <About v-if="page === 2" :lang="lang"/>
        <Projects v-if="page === 3" :lang="lang" />
      </div>
    </div>
  </div>
</template>
