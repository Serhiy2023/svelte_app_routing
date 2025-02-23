<script>
    import { page } from '$app/stores';
    import { derived } from 'svelte/store';
  
  const slug = derived(page, ($page) => decodeURIComponent($page.params?.slug || "Неизвестная страница"));
  </script>
   <a href="/">Back </a>
  <style>
   
  </style>