# React: docs, tips and tricks
Each folder contains a README.md for a dedicated topic.

### Overview

- React is designed like a downfacing tree of components
- Components are special cases of other components (Dialog --special--> WelcomeDialog --special--> WelcomeDialog_PremiumMember)
- The information flows down over parameter 'props'
- There are stateful and stateless components
    - Stateful components have their own state-object that contains data that changes over time
    - They get rerendered
- Data gets handed from top to bottom
    - Shared data should be defined in the components where its 'dividing' itself
    - -> There sould always be a single source of truth
