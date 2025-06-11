# Adapter

The Adapter pattern is represented as a **span** in a category of types, where an intermediate object $\mathrm{Ad}$ (Adapter) bridges incompatible types $A$ (Adaptee) and $T$ (Target) via morphisms $c: A \to \mathrm{Ad}$ (construction) and $i: \mathrm{Ad} \to T$ (interpretation). The adaptation is the composition $i \circ c: A \to T$, enabling $A$ to be used as $T$.

### Category-Theoretic Representation  
**Let**:  
- $\mathcal{C}$ be a **category of types and computable functions**.  
- $A, T \in \mathcal{C}$ denote the **Adaptee** and **Target** types, respectively.  
- $\mathrm{Ad} \in \mathcal{C}$ denote the **Adapter type**.  
- Morphisms:  
  - $c: A \to \mathrm{Ad}$ (constructs an Adapter from an Adaptee),  
  - $i: \mathrm{Ad} \to T$ (interprets the Adapter as a Target).  
- The **adaptation** is the composition $i \circ c: A \to T$.  

### Explanation  
1. **Span Structure**:  
   The Adapter $\mathrm{Ad}$ is an intermediate object connecting $A$ and $T$ via $c$ and $i$, forming a span:  
   $$A \xrightarrow{c} \mathrm{Ad} \xrightarrow{i} T.$$  
2. **Morphisms as Conversions**:  
   - $c$ wraps $A$ into $\mathrm{Ad}$ (e.g., storing $A$ as a member in $\mathrm{Ad}$).  
   - $i$ coerces $\mathrm{Ad}$ to $T$ (e.g., via subtyping or explicit casting).  
3. **Composition as Adaptation**:  
   $i \circ c$ converts $A$ to $T$, allowing $A$ to masquerade as $T$.  

### Why This Works  
- **Interface Compatibility**:  
  $i$ ensures $\mathrm{Ad}$ fulfills $T$'s interface, while $c$ embeds $A$ into $\mathrm{Ad}$.  
- **Decoupling**:  
  Clients depend only on $T$ (via $i$), oblivious to $A$ and $\mathrm{Ad}$.  
- **Reusability**:  
  New adapters for different $A$ extend $\mathrm{Ad}$ without modifying $T$ or clients.  

### Validity  
1. **Morphism Composition**:  
   In $\mathcal{C}$, $i \circ c$ is a valid morphism (function composition).  
2. **Object Closure**:  
   $\mathrm{Ad}$, $A$, $T$ are objects in $\mathcal{C}$, and $c$, $i$ are morphisms in $\mathcal{C}$.  
3. **Behavioral Faithfulness**:  
   The span $A \to \mathrm{Ad} \to T$ mirrors the Adapter’s runtime behavior:  
   - $c$ constructs the adapter,  
   - $i$ exposes it as the target type.  
