<script>

    import { createEventDispatcher } from 'svelte';
    let dispatch = createEventDispatcher();
    
    export let items;
    export let activeItem;
  
  </script>
  
  <div class="tabs">
    <ul>
      {#each items as item}
        <li on:click={() => dispatch('tabChange', item)}>
          <div class:active={item === activeItem}>{ item }</div>
        </li>
      {/each}
    </ul>
  </div>
  
  <style>
    ul{
      display: flex;
      justify-content: center;
      padding: 0;
      list-style-type: none;
    }
    li{
      margin: 0 16px;
      font-size: 18px;
      font-family: "Poppins", Sans-serif;
      font-weight: bold;
      color: #FEFEFE;
      cursor: pointer;
    }
    li:hover {
      color: #F58737;
    }
    .active{
      color: #F58737;
    }
  </style>