# Dynamic Styled Buttons in SvelteKit

## Overview

This project is an experiment in creating dynamically styled buttons using SvelteKit. It demonstrates how to create a reusable button component that can change its appearance based on a JSON configuration file, without requiring changes to the component's code.

## Key Features

- Dynamic button styling based on JSON configuration
- Support for 'filled' and 'outline' button styles
- Easy to extend for additional button types
- Reactive styling updates when configuration changes

## Project Structure

- `src/lib/components/SdButtonL.svelte`: The main button component
- `src/lib/data/button-styles.json`: JSON configuration for button styles
- `src/routes/+page.svelte`: Example usage of the button component

## How It Works

1. The `SdButtonL.svelte` component reads styles from a JSON configuration file.
2. It generates CSS dynamically based on this configuration.
3. The generated CSS is injected into the component using Svelte's reactive statements.
4. Buttons automatically update their appearance when the JSON configuration changes.

## Experiment Notes

This project is an experiment in leveraging AI assistance for development. The initial implementation and subsequent refinements were developed through a conversation with an AI assistant (Claude). This approach was used to explore:

- Rapid prototyping of ideas
- Problem-solving in Svelte/SvelteKit development
- Exploring dynamic styling techniques in Svelte

## Future Improvements

- Add more button types and styles
- Implement theme switching functionality
- Explore performance optimizations for style generation



## Contributions

This is an experimental project, but suggestions and improvements are welcome. Feel free to open an issue or submit a pull request.