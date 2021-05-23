# Steps
1. Break UI in component hierarchy
2. Build static version with no interactivity (dont use state yet)
3. Define minimal set of mutable state properties
4. Decide wich component should hold the state
    - Identify every component that renders something based on that state
    - Find a common owner component
    - Either the common owner or another component higher up in the hierarchy should own the state
    - If you can’t find a component where it makes sense to own the state, create a new component
5. Add Inverse Data Flow