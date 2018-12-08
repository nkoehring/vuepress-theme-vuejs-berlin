<template>
  <div id="home">
    <article class="content-container">
      <Content />
    </article>
  </div>
</template>

<style>
#home {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-evenly;
  height: 100%;
  margin-top: 100vh;
  background: white;
}

#home > footer {
  margin-top: 2em;
  font-size: 1rem;
  text-align: right;
}

#home h2 {
  margin-top: 3em;
  font-size: 1.2rem;
}
</style>

