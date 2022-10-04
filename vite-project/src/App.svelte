<script lang="ts">
  import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
  import Schedule from './components/Schedule.svelte';
  import Generate from './components/Generate.svelte';
  import Update from './components/Update.svelte';
  import Tabs from './shared/Tabs.svelte';
  
  let items = ['Schedule','Generate','Update'];
  let activeItem = 'Schedule';
  const tabChange = (e) => activeItem = e.detail;
  
</script>

<div class="navbar">
  <Header />
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
</div>

<main>
  {#if activeItem === 'Schedule'}
  <Schedule />
  {:else if activeItem === 'Generate'}
  <Generate />
  {:else if activeItem === 'Update'}
  <Update />
  {/if}
</main>

<Footer />

<style>
  .navbar {
    background: #543BE1;
    align-items: center;
    flex: 1;
    display: flex;
    padding-left: 5rem;
    padding-right: 5rem;
    padding-top: 1rem;
    padding-bottom: 1rem;
  }
</style>