<script>
    import SdButton from '$lib/components/SdButton.svelte';
    import SdButtonL from '$lib/components/SdButtonL.svelte';
  </script>
  
  <h1>Welcome to SvelteKit</h1>
  <p>Here are some dynamically styled buttons:</p>
  
  <div class="button-container">
    <SdButtonL type="primary">Primary Button</SdButtonL>
    <SdButtonL type="secondary">Secondary Button</SdButtonL>
  </div>
  
  <style>
    .button-container {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
  </style>