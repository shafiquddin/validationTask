<template>
  <div>
    <header>
      <h2>March 27 2023</h2>
    </header>
    <main>
      <the-form></the-form>
    </main>
  </div>
</template>

<script>
import TheForm from "./components/TheForm.vue";

export default {
  components: {
    TheForm,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

header {
  background: #d54343;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}
header h2 {
  color: white;
}
main {
  background-image: url("../assets/background.jpg");
}
</style>
