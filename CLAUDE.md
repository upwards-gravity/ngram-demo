# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

N-Gramm Werkstatt is an interactive educational tool for visualizing n-gram language models and text generation. It demonstrates how statistical text generation works using 1-gram, 2-gram, and 3-gram models with temperature-controlled sampling.

## Architecture

This is a **single-file React application** (`ngram.html`) that:
- Loads React 18, ReactDOM, and Babel via CDN
- Uses inline `<script type="text/babel">` for JSX transpilation in the browser
- Contains all CSS as inline styles and a minimal `<style>` block
- Requires no build step - open directly in a browser

### Key Components

- **NGramApp**: Main application component managing state for text input, n-gram selection, temperature, and generation history
- **NgramPill**: Displays individual n-grams with count badges and highlight states
- **SamplingViz**: Visualizes the probability distribution for next-word sampling

### Core Functions

- `tokenize/detokenize`: Split text into tokens (handling punctuation) and reconstruct
- `buildNgrams`: Construct frequency map of n-grams from token array
- `getCandidates`: Find possible next words given current context
- `applyTemperature`: Apply softmax temperature to probability distribution
- `sampleFromDist`: Sample next word from probability distribution

### State Management

Uses React refs for mutable state that shouldn't trigger rerenders:
- `histRef`: Array of generation steps (each with textWords, distribution, picked word, context)
- `viewRef`: Current position in history for step-through navigation
- `autoRef/autoOnRef`: Auto-play timer management

## Development

Open the HTML file directly in a browser. No server or build process required.

## Language

The UI is in German. Key terms:
- Quelltext = Source text
- Temperatur = Temperature (sampling randomness)
- Anfangstext = Initial/prompt text
- Nächstes Wort = Next word
