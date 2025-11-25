
# **📘 Knowledge Representation & Reasoning — Full Exam Notes (~5000+ Words)**

*(Knowledge-Based Agents, Propositional Logic, Theorem Proving, CNF/DNF, Horn Clauses, Forward & Backward Chaining, Knowledge Engineering in FOL, Expert Systems)*

---

# **1. Knowledge Representation & Reasoning (KRR)**

Knowledge Representation and Reasoning (KRR) is a core subfield of Artificial Intelligence concerned with representing information about the world in a form that a computer can understand and reason with. KRR lies at the heart of intelligent systems because intelligence is fundamentally the ability to **use knowledge** to make **correct decisions**.

KRR answers two major questions:

1. **How do we represent knowledge?**
   (Using logic, rules, semantic networks, frames, ontologies, etc.)

2. **How do we reason using that knowledge?**
   (Deriving new facts, answering queries, making decisions.)

Humans reason using common sense, experience, and perceptions. A machine must rely on a **formal representation** that is accurate, unambiguous, and computationally manageable.

The main purposes of KRR:

* Model the world in a structured format.
* Provide a foundation for reasoning algorithms.
* Enable inference: deriving new information from known facts.
* Support decision-making in autonomous systems.
* Organize information logically for expert systems, planning, and diagnosis.

Logic — specifically Propositional Logic and First-Order Logic — is the most widely used method due to its mathematical precision and ability to support formal inference.

---

# **2. Knowledge-Based Agents (KBA)**

Knowledge-Based Agents (KBAs) are a type of intelligent agent that contain an explicit representation of knowledge and use reasoning mechanisms to decide actions.

They operate based on:

* **Knowledge Base (KB)**
* **Inference Engine**
* **Perception (Sensors)**
* **Action (Actuators)**

A KBA behaves similarly to an intelligent human:

1. It **perceives** its environment.
2. It **updates** the knowledge base.
3. It **reasons** about what action is best.
4. It **acts** accordingly.

---

## **2.1 Components of a Knowledge-Based Agent**

### **1) Knowledge Base (KB)**

A KB contains facts and rules about the world:

* Facts represent known truths.
* Rules describe relationships and inference patterns.
* Sentences are written in a Knowledge Representation Language (KRL) such as Propositional Logic or First-Order Logic.

### **2) Inference Engine**

The reasoning mechanism that derives new facts using the KB.

Two core reasoning styles:

* **Deductive reasoning** (from general → specific)
* **Inductive reasoning** (from specific → general)
* **Abductive reasoning** (inferring the best explanation)

### **3) TELL/ASK Mechanism**

A standard interface:

* **TELL(KB, sentence)**: Add new facts to the KB.
* **ASK(KB, query)**: Infer whether the query is implied by the KB.

This makes the KB dynamic, meaning it grows over time as the agent learns from perception.

### **4) Architecture**

1. Agent receives percept.
2. Agent **TELLs** the KB about percept.
3. Agent **ASKs** the KB for best action.
4. Reasoning is performed.
5. Agent **TELLs** KB which action it selected.
6. Action is performed.

This loop allows continuous reasoning and interaction.

---

# **3. Propositional Logic (PL)**

Propositional Logic is the simplest form of logic used in AI. It deals with **propositions** — statements that are either TRUE or FALSE.

Examples:

* P: “It is raining.”
* Q: “The light is on.”

PL uses:

* **Atomic Propositions**: Basic indivisible statements.
* **Compound Propositions**: Formed by logically combining atomic propositions.

---

## **3.1 Syntax of Propositional Logic**

A propositional sentence can be:

* Atomic proposition (P)
* Compound proposition (e.g., P ∧ Q)

### **Logical Connectives**

* ¬P  (NOT P)
* P ∧ Q  (AND)
* P ∨ Q  (OR)
* P → Q  (Implication)
* P ↔ Q  (Biconditional)

---

## **3.2 Semantics / Truth Tables**

Truth tables define the truth value of complex propositions based on atomic propositions.

Example (AND):

| P | Q | P ∧ Q |
| - | - | ----- |
| T | T | T     |
| T | F | F     |
| F | T | F     |
| F | F | F     |

---

## **3.3 Properties of Connectives**

* **Commutativity**: P ∧ Q = Q ∧ P
* **Associativity**: (P ∧ Q) ∧ R = P ∧ (Q ∧ R)
* **Distributivity**: P ∧ (Q ∨ R) = (P ∧ Q) ∧ (P ∧ R)
* **De Morgan’s Laws**:
  ¬(P ∧ Q) = ¬P ∨ ¬Q

---

## **3.4 Limitations of Propositional Logic (from slides)**

PL is limited in representing:

* **Quantifiers (∀, ∃)**
* **Relationships between objects**
* **Properties of objects**
* **Complex structures or domains**

This leads us to First-Order Logic (FOL), which is far more expressive.

---

# **4. Propositional Theorem Proving**

Theorem proving is the process of checking whether:

### **KB ⊨ α**

(Does the knowledge base logically entail α?)

The two most common approaches:

---

## **4.1 Model Checking**

Check all possible truth assignments (brute-force).
If α is true in every model where KB is true → entailed.

Downside:
Exponential time complexity.

---

## **4.2 Inference / Proof-Based Approach**

Focused on proof rules that derive new conclusions.

Common rules:

* **Modus Ponens**: From P → Q and P, infer Q.
* **And-Elimination**
* **Or-Introduction**
* **Resolution** (most powerful rule)

The most widely used rule for propositional theorem proving is **Resolution**, which requires **CNF** representation.

---

# **5. Converting to CNF & DNF**

CNF (Conjunctive Normal Form) and DNF (Disjunctive Normal Form) are standardized structures used in logical inference.

---

# **5.1 Conjunctive Normal Form (CNF)**

A CNF sentence is a conjunction of disjunctions:
(Clause1) ∧ (Clause2) ∧ (Clause3)

Example:
(P ∨ ¬Q) ∧ (R ∨ S ∨ T)

### **Steps to Convert Any Formula to CNF**

1. Eliminate ↔
2. Eliminate →
3. Push ¬ inward (using De Morgan’s Laws)
4. Apply distributive rules
5. Flatten parentheses

CNF is required for **Resolution Theorem Proving**.

---

# **5.2 Disjunctive Normal Form (DNF)**

DNF is ORs of ANDs:
(P ∧ Q ∧ R) ∨ (A ∧ ¬B)

Used in some classification systems and decision tables.

---

# **6. Horn Clauses**

Horn clauses are a special type of clause that contain:

* At most **one positive literal**

Forms:

1. **Definite clause**: A ∧ B ∧ C → D
2. **Fact**: D
3. **Goal clause**: ¬A ∨ ¬B ∨ ¬C (used in backward chaining)

Importance:

* Efficient for inference
* Used in logic programming (Prolog)
* Basis for Forward & Backward chaining algorithms

---

# **7. Forward & Backward Chaining**

These are reasoning strategies used especially with Horn clauses.

---

# **7.1 Forward Chaining (Data-Driven Reasoning)**

Starts from **known facts**, applies rules → generates new facts.

Process:

1. Identify applicable rules.
2. Add conclusions to the KB.
3. Repeat until:

   * Goal found, or
   * No new facts can be generated.

Used in:

* Production systems
* Expert systems
* Situation where data is abundant

Advantages:

* Good for diagnosis and monitoring.

---

# **7.2 Backward Chaining (Goal-Driven Reasoning)**

Starts from a **goal** and works backward.

Procedure:

1. Check if goal is already known.
2. If not, find rule that concludes it.
3. Recursively check if premises of that rule can be proven.

Used in:

* Prolog
* Theorem proving
* Query answering systems

Advantages:

* Efficient when goal-oriented.
* Ignores irrelevant data.

---

# **8. Knowledge Engineering in First-Order Logic**

First-Order Logic (FOL) extends propositional logic by adding:

* **Predicates**
* **Functions**
* **Variables**
* **Quantifiers**

FOL can express statements such as:

* “All humans are mortal”
  ∀x (Human(x) → Mortal(x))

* “There exists a person who owns a dog”
  ∃x ∃y (Person(x) ∧ Dog(y) ∧ Owns(x, y))

---

## **8.1 Syntax of FOL**

Elements:

* **Constants**: Ali, 3
* **Variables**: x, y
* **Predicates**: Brother(Ali, Umer)
* **Functions**: Father(John)
* **Connectives**
* **Quantifiers**

---

## **8.2 Semantics of FOL**

Semantics defines meaning:

* Domain: set of all objects
* Interpretation: maps symbols → objects/relations

---

## **8.3 Atomic Sentences**

Predicate(term1, term2)

Examples:

* Cat(Leo)
* Brother(Ali, Umer)
* Greater(3, 2)

---

## **8.4 Complex Sentences**

Formed using connectives:

* P ∧ Q
* ¬P
* P → Q
* ∀x P(x)

---

## **8.5 Inference in FOL**

Inference rules include:

* **Modus Ponens**
* **Universal Elimination/Instantiation**
* **Existential Introduction**
* **Existential Instantiation**
* **Universal Generalization**

---

## **8.6 Substitution & Unification**

### **Substitution**

Replacing a variable with a term:
P(x) → P(John)

### **Unification**

Finding substitutions that make two expressions identical.

Example:
UNIFY(King(x), King(John))
→ {x/John}

Most General Unifier (MGU) is the simplest substitution that works.

---

# **9. Expert Systems**

Expert Systems are AI programs that replicate the decision-making ability of human experts in a specific domain.

Examples:

* Medical diagnosis system
* Credit approval system
* Fault detection in machinery

---

## **9.1 Components of Expert Systems**

### **1. Knowledge Base**

Contains:

* Rules (if-then)
* Facts
* Domain expertise

### **2. Inference Engine**

Reasoning mechanism using:

* Forward chaining
* Backward chaining

### **3. User Interface**

Communicates with users.

### **4. Explanation System**

Explains reasoning steps:

* “Why this conclusion?”
* “How was diagnosis made?”

---

## **9.2 Benefits**

* High accuracy
* Consistency
* Works 24/7
* Captures rare domain knowledge

---

## **9.3 Limitations**

* Hard to update
* Dependent on expert knowledge
* Lacks general intelligence

---

# **10. Wumpus World (From Slides)** *(Exam theory relevance)*

Wumpus World is a classic environment illustrating:

* Knowledge-based agents
* Partial observability
* Reasoning using logic
* Uncertainty

It is a grid-based layout where:

* Agent must avoid pits
* Avoid Wumpus monster
* Detect breeze, stench, glitter (percepts)
* Grab gold and leave

The agent uses logical reasoning:

* Breeze ⇒ Pit in adjacent cells
* Stench ⇒ Wumpus nearby
* No breeze/stench ⇒ Safe cells

This perfectly demonstrates KBA and reasoning rules.

---

# **11. Comprehensive Summary for Exam Revision**

---

## **Knowledge-Based Agents**

* Store and use knowledge to decide actions.
* Use TELL/ASK interface.
* Use inference engine for reasoning.
* KB contains facts, rules.

---

## **Propositional Logic**

* Propositions: True/False.
* Connectives: AND, OR, NOT, →, ↔
* Truth tables define semantics.
* Limited expressiveness.

---

## **Propositional Theorem Proving**

* Model checking (brute force)
* Inference rules (modus ponens)
* Resolution (requires CNF)

---

## **CNF & DNF**

* CNF: AND of ORs.
* DNF: OR of ANDs.
* CNF used for resolution.

---

## **Horn Clauses**

* At most one positive literal.
* Used in rule-based reasoning.
* Ideal for forward/backward chaining.

---

## **Forward Chaining**

* Data-driven.
* Starts with known facts.
* Applies rules to derive new facts.

---

## **Backward Chaining**

* Goal-driven.
* Starts with goal.
* Works backward to find supporting facts.

---

## **Knowledge Engineering in FOL**

* FOL → expressive logic.
* Uses predicates, quantifiers.
* Supports substitution and unification.
* Core inference rules: UI, EI, UG.

---

## **Expert Systems**

* Mimic human experts.
* KB + Inference Engine.
* Forward/Backward chaining used.
* Applications in medicine, finance, engineering.
