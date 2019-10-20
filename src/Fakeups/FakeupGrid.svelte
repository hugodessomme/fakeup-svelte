<script>
  import FakeupItem from "./FakeupItem.svelte";

  export let fakeups;
</script>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>

<section id="fakeups">
  {#each fakeups as fakeup}
    <FakeupItem
      title={fakeup.title}
      subtitle={fakeup.subtitle}
      description={fakeup.description}
      imageUrl={fakeup.imageUrl}
      address={fakeup.address}
      contactEmail={fakeup.contactEmail} />
  {/each}
</section>
