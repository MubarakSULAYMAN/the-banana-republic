<template>
  <section class="content-container flex-row">
  <div class="wrapper">
    <h1>My world today</h1>

    <p>
      Labore praesentium cumque voluptates ratione. Eos corporis sequi sunt,
      mollitia molestiae cumque qui distinctio cum? Delectus autem quo dolorem
      voluptatibus quaerat odio doloribus atque iusto, in a ab neque placeat
      totam quidem voluptates eaque, necessitatibus beatae temporibus
      repellendus quibusdam maiores.
      <strong>
        <a href="http://" target="_blank" rel="noopener noreferrer">
          View all days,
        </a>
      </strong>
      aspernatur similique exercitationem, eligendi qui dolor dolorum ea, autem
      odit repellat accusamus consequatur animi culpa enim doloribus. Magnam,
      sit reiciendis aliquid accusantium suscipit modi amet illum distinctio
      pariatur commodi, sapiente architecto accusamus temporibus, voluptate
      deserunt magni! Libero officiis obcaecati laudantium incidunt qui
      architecto labore perferendis cumque voluptates facere quaerat dolorem,
      sed ullam recusandae excepturi exercitationem, illum aliquid quasi.
    </p>
  </div>
  </section>
</template>

<script>
export default {};
</script>

<style scoped>
::selection {
  color: var(--white);
  background-color: var(--yellow);
}

.content-container {
  background-color: var(--orange);
}

.wrapper {
  margin: 100px;
}

h1 {
  margin-bottom: 50px;
  font-size: var(--text-lg);
  font-weight: 700;
}

strong {
  font-weight: 600;
}

strong a {
  text-decoration: underline;
}

strong a:hover {
  text-decoration: none;
}

@media only screen and (max-width: 768px) {
  .wrapper {
    margin: auto 60px;
  }
}

@media only screen and (max-width: 425px) {
  .wrapper {
    margin: 20px;
  }

  h1 {
    margin-bottom: 20px;
  }
}
</style>
