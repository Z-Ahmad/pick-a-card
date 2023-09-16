<!-- Card.svelte -->
<script>
  export let color;
</script>

<div class="card" style="background-color: {color}"></div>

<style>
  .card {
    width: 80px; /* Adjust as needed for card size */
    height: 120px; /* Adjust as needed for card size */
    border-radius: 5px;
  }
</style>
