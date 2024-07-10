<script>
  import { onMount } from 'svelte';
  import buttonStyles from '../data/button-styles.json';

  export let type = 'primary'; // Can be 'primary' or 'secondary'

  const colors = {
    primary: '#007bff',
    secondary: '#6c757d'
  };

  let styles = buttonStyles['button-styles'];
  let styleString = '';

  $: {
    styleString = Object.entries(colors).map(([buttonType, color]) => {
      const style = styles[buttonType];
      return `
        .dynamic-btn.${buttonType} {
          ${style === 'filled' 
            ? `background-color: ${color}; color: white; border: none;` 
            : `background-color: transparent; color: ${color}; border: 2px solid ${color};`
          }
        }
        .dynamic-btn.${buttonType}:hover {
          ${style === 'filled'
            ? `background-color: ${color}cc;`
            : `background-color: ${color}22;`
          }
        }
      `;
    }).join('\n');
  }
</script>

<button class={`dynamic-btn ${type}`}>
  <slot></slot>
</button>

<style>
  /* Fallback styles */
  .dynamic-btn {
    padding: 10px 20px;
    font-size: 16px;
    border-radius: 4px;
    cursor: pointer;
  }
</style>

<svelte:element this="style">
  {styleString}
</svelte:element>