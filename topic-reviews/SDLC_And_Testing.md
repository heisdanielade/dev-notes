# 🛠️ Software Development & Testing

**Software testing** is the process of _inspecting_ the _correctness_ and _completeness_ of a computer software. It ensures that the _actual product_ matches the _expected product_ and is _defect-free_.

## Software Development Life Cycle

SDLC (**Software Development Life Cycle**) is a structured process for planning, creating, testing, deploying, and maintaining software systems.<br>
It defines how software is developed from start to finish; ensuring quality, efficiency, and predictability.

```bash
 _______________________              _______________              _________________
|                       |            |               |            |                 |
|  Requirement Analysis |    --->    |    Design     |    --->    |  Development    |
|_______________________|            |_______________|            |_________________|
                                                                           |
                                                                           v
                                                                    ________________
                                                                   |                |
                                                                   |    Testing     |
                                                                   |________________|
              ________________              _________________            |
             |                |            |                 |           |
             |  Maintenance   |    --->    |   Deployment    |    <-----
             |________________|            |_________________|

```

- **Planning:** defines project's goals, scope & feasibility.

  - Identify requirements
  - Estimate costs
  - Set timelines
  - Assess potential risks
  - Involves stakeholders & team leads

- **Requirement Analysis:** analyze and document user needs & business requirements.

  - Create a detailed specification document
  - Involves project manager and senior members of the team.

- **Design:**

  - **High-level:** overview of software structure i.e., `system architecture`
  - **Low-level:** detailed description of individual components and how each should work i.e., `database structure`, `user interfaces` & `tech stack`.

- **Testing:** After software is built, it is sent to the QA/Test team to rigorously test the software to find and fix bugs, ensure the software meets the requirements and verify it's _functionality_, _security_, and _performance_.

  - Manual and/or Automation testing
  - Done by `QA specialist`, `QA engineers` & `Software testers` alongside the developers.

- **Deployment:** Once the software is approved for release i.e., _defect-free_, _satisfied requirements_, it is deployed to a production environment.

  - Done by `DevOps engineers` through techniques like **CI/CD**.

- **Maintenance:** Post-deployment, the software enters the maintenance phase where teams
  - Provide updates
  - Address bugs and provide fixes
  - Ensure the software meets user needs over time.

### Models of SDLC

#### 1. Waterfall Model

Linear approach whereby each phase of DLC is _executed sequentially_. Best for projects with well-defined requirements, minimal expected changes, and quality is more important than timeline and/or costs.

```bash
   Stage 1 --> Stage 2 --> Stage 3 --> Stage 4 --> Stage 5 --> Stage 6
```

- **Disadvantages:**
  - Backtracking is highly discouraged
  - Longer timelines
  - Not suitable for long-term projects where requirements change.

#### 2. Boehm (Spiral) Model

It involves combining iterative development with risk analysis. The project is divided into `spirals` or cycles, each including planning, risk assessment, development and evaluation. Best for large-scale and comples projects with significant risks or uncertainty.

#### 3. Agile Model

A flexible, iterative approach where development is broken into smaller cycles called `sprints` (typically 2-4 weeks long). Best for projects, requiring frequent updates, user feedback or eveolving requirements.

#### 4. V-model (Verification and Validation)

Each development phase on the left side has a corresponding testing phase on the right side. Testing is planned and executed alongside development, ensuring quality from the start.

```bash
    Req. Analysis        Acceptance Test
         \                   /
          \                 /
       System Design    System Test
            \             /
             \           /
         Module Dev   Unit Test
               \      /
                \    /
                 \  /
```

<br>

## Principles of Software Testing

#### 1. Testing shows the presence of defects, not their absence

Testing can reveal bugs, but it can never prove that the software is completely error-free.<br>
The goal is risk reduction, not perfection.

#### 2. Exhaustive testing is impossible

You can’t test everything; every input, path, or combination.<br>
Focus testing on risk-based and priority-driven areas.

#### 3. Early testing saves time and money

The earlier a defect is found (e.g., during requirements or design), the cheaper it is to fix.<br>
`Shift-left testing`, involve testers from the start.

#### 4. Defects cluster together

A small number of modules usually contain most of the bugs.<br>
Use `Pareto’s principle (80/20 rule)` to focus testing on these hotspots.

#### 5. Beware of the pesticide paradox

Running the same tests over time finds fewer new bugs.<br>
Regularly review and evolve test cases to stay effective.

#### 6. Testing depends on context

The approach varies with the system:

- Safety-critical (e.g., aviation) ≠ Mobile app ≠ Web startup.<br>
  Tailor test depth, tools, and techniques accordingly.

#### 7. Absence-of-errors fallacy

Finding no bugs doesn’t mean the software is useful or meets requirements.<br>
Software must also solve the right problem.
