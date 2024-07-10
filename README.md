# Dynamic Styled Buttons in SvelteKit

## Overview

This project is an experiment in creating dynamically styled buttons using SvelteKit. It demonstrates how to create reusable button components that can change their appearance based on a JSON configuration file, without requiring changes to the component's code.

## Key Features

- Dynamic button styling based on JSON configuration
- Support for 'filled' and 'outline' button styles
- Easy to extend for additional button types
- Reactive styling updates when configuration changes
- Two versions of the button component: locked and customizable

## Project Structure

- `src/lib/components/SdButtonL.svelte`: The locked button component
- `src/lib/components/SdButton.svelte`: The customizable button component
- `src/lib/data/button-styles.json`: JSON configuration for button styles
- `src/routes/+page.svelte`: Example usage of the button components

## How It Works

1. The button components read styles from a JSON configuration file.
2. They generate CSS dynamically based on this configuration.
3. The generated CSS is applied to the buttons, either through injected styles or CSS custom properties.
4. Buttons automatically update their appearance when the JSON configuration changes.

## Button Implementations

### 1. Locked Version (SdButtonL.svelte)

The locked version uses dynamic style generation in the component's script:

```svelte
<script>
  import { onMount } from 'svelte';
  import buttonStyles from '../data/button-styles.json';

  export let type = 'primary';

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
          /* Dynamic styles here */
        }
      `;
    }).join('\n');
  }
</script>

<button class={`dynamic-btn ${type}`}>
  <slot></slot>
</button>

<svelte:element this="style">
  {styleString}
</svelte:element>
```

- Styles are generated based on the JSON configuration and injected using `<svelte:element this="style">`.
- This approach prevents easy override of styles by users of the component.
- It's more secure and ensures consistent styling across the application.

### 2. Customizable Version (SdButton.svelte)

The customizable version uses CSS custom properties and classes:

```svelte
<script>
  import { onMount } from 'svelte';
  import buttonStyles from '../data/button-styles.json';

  export let type = 'primary';

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

  .outline {
    background-color: transparent;
    color: var(--button-color);
    border: 2px solid var(--button-color);
  }

  /* Hover styles */
</style>
```

- This version uses CSS classes and custom properties, making it more open to customization.
- Users can easily override styles or extend the component's appearance.
- It's more flexible but less controlled, potentially leading to inconsistent styling if not managed carefully.

## Comparison and Use Cases

- The locked version (SdButtonL) is superior for maintaining strict design consistency across an application or when providing a component library where you want to ensure users don't accidentally break the intended styling.
- The customizable version (SdButton) is better suited for projects where you want to provide users with more flexibility to adapt the buttons to their specific needs.

Choose the version that best fits your project's requirements for consistency vs. flexibility.

## Experiment Notes

This project is an experiment in leveraging AI assistance for development. The initial implementation and subsequent refinements were developed through a conversation with an AI assistant (Claude). This approach was used to explore:

- Rapid prototyping of ideas
- Problem-solving in Svelte/SvelteKit development
- Exploring dynamic styling techniques in Svelte
- Comparing different approaches to component design (locked vs. customizable)

## Future Improvements

- Add more button types and styles
- Implement theme switching functionality
- Explore performance optimizations for style generation
- Create a hybrid approach that balances consistency and customizability

## Getting Started

1. Clone the repository
2. Run `npm install` to install dependencies
3. Run `npm run dev` to start the development server
4. Navigate to `http://localhost:5173` to view the buttons

## Contributions

This is an experimental project, but suggestions and improvements are welcome. Feel free to open an issue or submit a pull request.

## License

[MIT License](LICENSE)