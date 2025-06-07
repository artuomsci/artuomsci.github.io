# Singleton

The Singleton pattern is represented as a **terminal object** in a category of types, enforcing unique global accessibility and type-level uniqueness via its universal property. This abstracts the pattern's core constraint—exactly one "point of access".

### Category-Theoretic Representation  
Let:
- $\mathcal{C}$ be a **category** where:  
  - Objects are types in the program.  
  - Morphisms $f : A \to B$ represent functional relationships (e.g., accessors or transformations).  
- $S \in \mathcal{C}$ denote the **Singleton type**.  
- $S$ be a **terminal object** in $\mathcal{C}$:  
  - For every object $A \in \mathcal{C}$, there exists a **unique morphism** $!_A : A \to S$.  

### Explanation  
1. **Terminal Object as Uniqueness Enforcer**:  
   The unique morphism $!_A : A \to S$ ensures $S$ is accessible from any type $A$, modeling the global access point (e.g., `getInstance()`).  
2. **No Instance Dependence**:  
   Morphisms define *type relationships*, not runtime instances. The uniqueness of $!_A$ encodes the Singleton’s "single access path" invariant.  
3. **Isomorphism Invariance**:  
   All terminal objects are isomorphic; thus, $S$ is unique up to isomorphism, reflecting that distinct Singleton types cannot interfere.  

### Why This Works  
- **Global Access Control**:  
  The universal property $\forall A \in \mathcal{C}.\, \exists!\, (A \to S)$ ensures $S$ is reachable from all contexts, mirroring the Singleton’s global scope.  
- **Compatibility Guarantee**:  
  For any morphism $f : A \to B$, commutativity $!_B \circ f = !_A$ forces consistent access paths (e.g., no "alternate instances").  
- **Extensibility**:  
  Adding new types to $\mathcal{C}$ automatically defines unique accessors to $S$ without modifying $S$.  

### Validity  
1. **Terminal Objects Exist**:  
   $\mathcal{C}$ is constructible (e.g., as the free category over program types), and terminal objects are well-defined in such categories.  
2. **Uniqueness Holds**:  
   Uniqueness of $!_A$ is enforced axiomatically, prohibiting incompatible access paths.  
3. **Compositionality**:  
   For $f : A \to B$ and $g : B \to S$, $g \circ f = !_A$ by the terminal object property, ensuring consistency.  

