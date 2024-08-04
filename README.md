# My code-guide

This document outlines the rules and best practices for code design, including naming conventions, folder structure, and file organization. The goal is to maintain a clean, consistent, and scalable codebase that adheres to the Feature-Sliced Design (FSD) methodology.

## 1. Folder Structure: Feature-Sliced Design (FSD)
All code should be organized following the Feature-Sliced Design pattern. This means that each feature should be self-contained, with its own folder containing all relevant components, styles, and other entities.

Entity Folder
Each entity folder should contain the core entity and its associated components.
Entities should use dot notation for naming, reflecting the structure of the entity.
Example:

```typescript
import { ProfileContentContainer } from "@/features/profile/components/containers/content.profile.container";

export const Profile = {
    Content: ProfileContentContainer,
};
```

### Features Folder Structure

Each feature folder must include the following subfolders:

  - components
    
    - containers: Smart components that manage state and logic. They are connected to the store and pass data to presentation components.
      
    - presentations: Dumb components responsible for displaying data. They receive data via props from containers.
      
  - store: Contains all state management related to the feature.
  - styles: Contains stylesheets specific to the feature.
  
Example:
```
organization/ 
   components
     containers
     presentations
   styles 
   store  
   create/
        components 
           containers
           presentations
       styles
       store
```

## 2. Naming Conventions
### File Naming
- Files must follow the naming convention: <type of component>.<entity name>.(container|presentation).tsx.
Examples:

```
content.profile.container.tsx
confirm-userpic-profile.container.tsx
upload-userpic.profile.presentation.tsx
```

### Component Naming
- Components should be exported without using default export.
- The component name should follow the format: ```<Entity><Type of Component><Container | Presentation>``` using camelCase.
Examples:

```
export const ProfileContentContainer = () => { /* component code */ };
export const ProfileUpdatePasswordContainer = () => { /* component code */ };
```

### Function Naming
- Functions used as event handlers must include the word handler at the end of the name, with a verb as the prefix (e.g., submitHandler, changeHandler).
## 3. Folder Naming
- Folder names for containers and presentations should be pluralized (i.e., containers, presentations).
- File names should use the singular form (i.e., container, presentation).

## 4. Widgets Folder Structure
The widgets folder should include:

- schema: Contains service entities essential for application development.
- types.ts: Includes TypeScript types and interfaces related to the widget.

The same folder structure logic applies here: global entities should not affect global values, only the current realization. Nested folders are organized to ensure an effective and scalable folder structure.
