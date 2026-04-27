# Design Description

## Application

This application enables users to compare job offers by calculating weighted scores across multiple compensation factors. Users can enter their current job details, add multiple job offers, adjust comparison weights, and view jobs ranked by score.

## Purpose

The system enables informed career decisions by accounting for cost of living differences and allowing side-by-side comparison of any two jobs with detailed breakdowns of salary, benefits, and calculated scores. Users can prioritize job attributes by adjusting weights for each compensation factor from 0 (no interest) to 9 (highest interest).

## Summary

The design uses five core classes:

| Class         | Responsibility                                                                              | Relationships                                      |
| ------------- | ------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| `Application` | Entry point that coordinates all user interactions and menu operations                      | Coordinates all other classes through associations |
| `JobsList`    | Manages the current job and collection of job offers                                        | Contains `Job` instances through composition       |
| `Jobs`        | Stores individual job attributes (title, company, salary, benefits, etc.)                   |                                                    |
| `Weights`     | Maintains comparison settings with integer values 0-9 for each factor                       |                                                    |
| `Calculator`  | Handles all computational logic (scoring, cost of living adjustments, ranking, comparisons) | Dependent on `Jobs` and `Weights`                  |

---

## Requirement 1: Main Menu

**Implementation:**

|Relevant Class|Description|Design Decisions|Items|
|---|---|---|---|
|`Application` operations|Entry point operations that coordinate menu actions|Centralizing menu coordination in one class simplifies navigation logic and delegates domain-specific operations to specialized classes.|- `editCurrentJob()` - enter or edit current job details<br>- `addJobOffer()` - enter new job offers<br>- `updateSettings()` - adjust comparison weights<br>- `getJobComparison()` - initiate job comparison (checks whether job offers exist by querying `JobsList` before proceeding)|

---

## Requirement 2: Current Job Details

**Implementation:**

| Relevant Class | Description                                  | Design Decisions                                                                                                                                                                               | List                                                                                                                                                                                                                                                                                                                                  |
| ----------------------- | -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Jobs` attributes       | Stores job attributes with appropriate types | Separating job data from job management follows single responsibility principle. `JobsList` owns the collection and current job reference, while `Jobs` focuses purely on data storage. | - `title: string`<br>- `company: string`<br>- `city: string`<br>- `state: string`<br>- `costOfLivingIndex: double`<br>- `annualSalary: double`<br>- `annualBonus: double`<br>- `stockOptionShares: integer`<br>- `wellnessStipend: double` ($0-$1200)<br>- `lifeInsurance: integer` (0-10%)<br>- `personalDevFund: double` ($0-$6000) |
| `JobsList` attributes   | Manages current job reference                |                                                                                                                                                                                         | - `current: Job` (current job)                                                                                                                                                                                                                                                                                                        |
| `JobsList` operations   | Saves and retrieves current job details      |                                                                                                                                                                                         | - `setCurrentJob(Job)` - saves job details (when users save or cancel, `Application` coordinates the workflow and returns to main menu)<br>- `getCurrentJob(): Job` - retrieves current job                                                                                                                                           |

---

## Requirement 3: Enter Job Offers

**Implementation:**

Job offers use the same `Jobs` class structure as current jobs (all 10 attributes).

|Relevant Class|Description|Design Decisions|Items|
|---|---|---|---|
|`JobsList` attributes|Stores job offers|Reusing the `Jobs` class for both current job and offers eliminates redundancy and improves maintainability. `JobsList` owns the collection, making it responsible for storage operations.|- `jobs: Job[]` - stores job offers|
|`JobsList` operations|Adds new offers to collection||- `addJob(Job)` - adds new offers to collection|
|`Application` workflow|Coordinates post-save workflow options|`Application` handles user workflow decisions without implementing storage logic directly.|- Enter another offer (calls `addJobOffer()` again)<br>- Return to main menu<br>- Compare new offer with current job (if current job exists) - uses `Calculator.compareJobs()`, passing new offer and current job as parameters|

---

## Requirement 4: Comparison Settings (Weights)

**Implementation:**

| Relevant Class         | Description                                                         | Design Decisions                                                                                                                                                                          | Items                                                                                                                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Weights` attributes   | Stores weight values for each compensation factor (0-9, default: 1) | Centralizing weights in a single class makes them accessible to `Calculator` for score computations. Using integer types matches the discrete 0-9 range specified in requirements. | - `weightSalary: integer` (0 = no interest, 9 = highest interest)<br>- `weightBonus: integer`<br>- `weightStockOptions: integer`<br>- `weightWellnessStipend: integer`<br>- `weightLifeInsurance: integer`<br>- `weightPersonalDevFund: integer` |
| `Weights` operations   | Modifies and retrieves weight values                                | String-based setters and getters provide flexibility for specifying which weight to modify without requiring separate operations for each factor.                                  | - `setWeight(String, integer)` - modifies individual weights with validation (0-9 range)<br>- `getWeight(String): integer` - retrieves weight values for calculations                                                                            |
| `Application` workflow | Coordinates settings adjustment workflow                            |                                                                                                                                                                                    | - Save and cancel operations that return to main menu                                                                                                                                                                                            |

---

## Requirement 5: Compare Job Offers

**Implementation:**

| Relevant Class          | Description                                      | Design Decisions                                                                                                                                                                           | Items                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `JobsList` operations   | Retrieves all jobs for ranking                   | `Calculator` owns all score-dependent logic, including ranking.                                                                                                                     | - `getAllJobs(): Job[]` - retrieves all jobs (offers plus current job if it exists)                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `Calculator` operations | Ranks jobs and generates comparison data         | Returning `Job[]` from `compareJobs()` keeps the design simple: GUI extracts the necessary attributes for table display. This avoids creating an additional ComparisonResult class. | - `rankJobs(Job[], Weights): Job[]` - takes job collection and returns jobs sorted by score (best to worst); ranked list displays title and company for each job, with current job clearly indicated<br>- `compareJobs(Job1, Job2, Weights): Job[]` - returns both jobs for comparison; comparison table displays: title, company, location (city and state), adjusted yearly salary (AYS), adjusted yearly bonus (AYB), stock option shares, wellness stipend, life insurance, personal development fund, job score (JS) |
| `Application` workflow  | Coordinates comparison workflow and user options |                                                                                                                                                                                     | - After viewing comparison, users can perform another comparison or return to main menu                                                                                                                                                                                                                                                                                                                                                                                                                                   |

**GUI considerations:** Display of the ranked list, current job indication, job selection interface, and comparison table formatting are GUI responsibilities. The design provides operations to retrieve the necessary data.

---

## Requirement 6: Job Score Calculation

**Implementation:**

|Relevant Class|Description|Design Decisions|Items|
|---|---|---|---|
|`Calculator` operations|Implements weighted job score formula and cost of living adjustments|Centralizing all calculation logic in `Calculator` promotes reusability and testability. The cost of living adjustment is separated into its own operation because it's used for both salary and bonus. `Calculator` depends on `Jobs` and `Weights` but doesn't store them, accessing their data through parameters passed from `Application`.|- `calculateScore(Job, Weights): double` - implements formula: `JS = (w1 × AYS + w2 × AYB + w3 × (SOS/3) + w4 × WS + w5 × (LI/100 × YS) + w6 × PDF) / (w1 + w2 + w3 + w4 + w5 + w6)` where: AYS = Adjusted Yearly Salary, AYB = Adjusted Yearly Bonus, SOS = Stock Option Shares, WS = Wellness Stipend, LI = Life Insurance, PDF = Personal Development Fund, YS = Yearly Salary (unadjusted), w1-w6 = Weight values (0-9)<br>- `calculateForCLI(double, double): double` - adjusts salary and bonus values for cost of living by dividing by `costOfLivingIndex`; called twice per job score calculation (once for salary producing AYS, once for bonus producing AYB)|

---

## Requirement 7: User Interface

**Implementation:**

This requirement specifies GUI quality attributes (intuitive and responsive interface) rather than application logic. Per assignment guidelines, GUI-specific classes are not required in the class diagram.

|Relevant Class|Description|Design Decisions|Items|
|---|---|---|---|
|`Application` operations|Provides entry points for user actions|The assignment explicitly allows omitting GUI-specific classes. Application logic classes provide sufficient interfaces for a GUI layer to interact with the domain model.|- Entry point operations for each menu action|
|`JobsList` operations|Provides data access operations||- Data retrieval operations that GUI components can call|
|`Calculator` operations|Provides computation operations|Responsiveness and intuitiveness are implementation qualities that depend on GUI technology choices, not class diagram structure.|- Score calculations, ranking, and comparison operations|

**Design approach:** The design supports an intuitive interface by separating concerns—GUI handles presentation and user interaction, while the class structure handles business logic and data management.

**Not directly shown:**

- View components (screens, forms, buttons, lists)
- Event handlers and UI controllers
- Layout and styling logic
- Input validation UI (though data type constraints exist in domain classes)

---

## Requirement 8: System Scope

**Implementation:**

The single-user, single-device scope is reflected throughout the design.

|Relevant Class|Description|Design Decisions|Items|
|---|---|---|---|
|`Application` design|Single instance entry point|Single-user scope simplifies the design significantly. Without multiple users, `Application` can directly reference `JobsList` and `Weights` without worrying about which user's data to access.|- No user authentication, session management, or multi-user data isolation|
|`JobsList` design|Single instance storage|Without cross-device requirements, no data synchronization or conflict resolution logic is needed.|- Maintains one current job and one collection of offers without user identifiers or ownership tracking|
|System constraints|Local-only operations||- No networking, synchronization, or cloud storage classes<br>- All data operations are local and immediate<br>- No concurrency control mechanisms needed (only one user interacts at a time)<br>- Data persistence, if implemented, would be local to the device|

**Assumptions:**

- No user authentication or access control required
- No multi-user data isolation or conflict resolution
- Data is stored locally on a single device
- No network communication or remote data access
- No concurrent access patterns or threading concerns

**Not directly shown:** This requirement constrains what is excluded from the system rather than what must be included. The absence of user management, networking, and synchronization classes reflects this scope limitation.

---

## Design Decisions Summary

**Architecture:**
- The five-class design uses a coordination pattern: `Application` serves as the orchestrator, delegating to specialized classes (`JobsList` for storage, `Calculator` for computation, `Weights` for configuration).
- This separation enables independent testing and modification of each concern.

**Relationships:**
- `Application` has associations to `JobsList`, `Weights`, and `Calculator` (enabling coordination).
- `JobsList` uses composition with `Jobs` (diamond notation) - `JobsList` owns and manages `Job` instances.
- `Calculator` has dependencies on `Jobs` and `Weights` (dashed arrows) - uses their data without owning them.
- These relationship types minimize coupling while maintaining necessary connections.