<script>
    import { page } from '$app/stores';
    import { derived } from 'svelte/store';
  
  const slug = derived(page, ($page) => decodeURIComponent($page.params?.slug || "Неизвестная страница"));
  let pageTitle = derived(page, $page => {
        return decodeURIComponent($page.url.pathname.slice(6));
    });
  </script>
  <h1>{$pageTitle}</h1>
   <a href="/" class="link">⬅ Back </a>
   
  <style>
   h1 {
    text-align: center;
   }
   .link{
    display: block;
    text-align: center;
  }
  </style>
