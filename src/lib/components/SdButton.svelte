<script>
    import { onMount } from 'svelte';
    import buttonStyles from '../data/button-styles.json';
  
    export let type = 'primary'; // Can be 'primary' or 'secondary'
  
    const colors = {
      primary: '#007bff',
      secondary: '#6c757d'
    };
  
    $: style = buttonStyles['button-styles'][type];
    $: color = colors[type];
  </script>
  
  <button class={`${type} ${style}`} style="--button-color: {color};">
    <slot></slot>
  </button>
  
  <style>
    button {
      padding: 10px 20px;
      font-size: 16px;
      border-radius: 4px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
  
    .filled {
      background-color: var(--button-color);
      color: white;
      border: none;
    }
  
    .filled:hover {
      opacity: 0.9;
    }
  
    .outline {
      background-color: transparent;
      color: var(--button-color);
      border: 2px solid var(--button-color);
    }
  
    .outline:hover {
      background-color: rgba(0, 0, 0, 0.1);
    }
  </style>