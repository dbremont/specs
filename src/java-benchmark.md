Specification

Order: Generate a Web Site - That Meet the Following Specs

## Objective

Produce a professional, expert-grade benchmark report website that presents empirical performance measurements of selected Java Standard Library collection implementations, specifically:

- java.util.ArrayList
- java.util.LinkedList
- Collections.synchronizedList(new ArrayList<>())

The report must be methodologically defensible, transparent, and reproducible, such that its conclusions can be evaluated, critiqued, and reproduced by JVM performance engineers and systems researchers.

## Validation Criteria

The generated benchmark report is considered valid only if:

- All assumptions are explicit
- All measurements are contextualized
- No charts are presented without explanation
- No conclusions exceed the scope of the data
- Reproduction is realistically possible

## Technical Specs

### Tech Stack

- **HTML:**
  * Pure, static, standards-compliant HTML5
  * No frameworks (React, Vue, Svelte, etc.)

- **CSS:**
  * Tailwind CSS (via CDN or compiled build)
  * No custom CSS frameworks

- **Visualization:**
  * Apache ECharts (explicit version declared)
  * Deterministic chart configuration (no random styling)

- **JavaScript:**
  * Minimal, modular, non-framework JS
  * Used only for:
    * Navigation state
    * Chart rendering
    * Theme toggling

### Layout and Navigation Requirements

#### Header (Persistent)

* Branding: **Java: Informe de Rendimiento**
* Benchmark Name: **ArrayList, LinkedList & SynchronizedList**
* Benchmark Litle Description: Java Standard Library Collections Benchmark: A Comprehensive Performance Analysis 
* Metadata & Tags:
	* Documention Version
 	* Version
* Interactive **Table of Contents (ToC)**:
  * Reflects document structure
  * Highlights the currently visible section
  * Allows direct section navigation (scroll-linked)

### Footer

-  Report version
-  Benchmark execution timestamp
-  Git commit hash or artifact version (if applicable)


### SEO and Metadata (Mandatory)

HTML <meta> tags:
- Description
- Keywords
- Author
- Viewport

Open Graph metadata for sharing

Structured data (schema.org/SoftwareSourceCode):

- Name
- Programming language
- Runtime platform
- Version
- License (if applicable)

### UX and Presentation Quality

- Dark and light modes (system-aware default)
- Mobile-responsive tables (horizontal scrolling, sticky headers)
- Explicit loading states for charts
- Graceful error boundaries for missing or malformed data
- Visual restraint:
	- No chart junk
 	- Consistent typography
	- Color-blind-safe palettes

### UI Quality

#### 6.1 Visual Hierarchy and Typography

* Clear, consistent visual hierarchy across all pages:

  * Section headers, subsections, captions, and body text must be visually distinguishable.
* Typography requirements:

  * Sans-serif, highly legible typeface (Tailwind default or equivalent).
  * Consistent font scale and line spacing.
  * Monospaced font for:

    * Code blocks
    * JVM flags
    * Command-line invocations
    * Configuration excerpts
* No decorative or novelty fonts.

#### 6.2 Layout Discipline

* Grid-based layout with consistent margins and spacing.
* Maximum readable line width for body text (avoid full-width paragraphs on large screens).
* Content density must be balanced:

  * No excessive whitespace.
  * No visual crowding of charts or tables.
* Charts, tables, and text must be aligned and grouped logically.

#### 6.3 Chart and Table Presentation

##### Charts

* Every chart must include:

  * Title
  * Axis labels with units
  * Legend (where applicable)
* Axes must be:

  * Clearly labeled
  * Non-misleading (no truncated axes unless explicitly justified)
* Color usage:

  * Consistent color mapping across charts
  * Color-blind-safe palette
  * No gradients, shadows, or decorative effects
* Animations:

  * Disabled or minimal
  * Must not affect interpretation or timing perception

##### Tables

* Tables must:

  * Include headers with units where applicable
  * Support horizontal scrolling on small screens
  * Use sticky headers for large datasets
* Numeric formatting:

  * Consistent precision
  * Aligned decimal points where possible
* Tables must not duplicate charts verbatim unless justified.


#### 6.4 Interaction and Navigation Quality

* Navigation must be:

  * Predictable
  * Stable
  * Free of layout shifts
* Interactive elements (tabs, ToC, theme toggle):

  * Must have clear affordances
  * Must not obscure content
* No unexpected behavior:

  * No auto-scrolling
  * No pop-ups or modal interruptions
  * No hover-only critical interactions

#### 6.5 Responsiveness and Device Support

* Fully usable on:

  * Desktop
  * Tablet
  * Mobile
* On smaller screens:

  * Charts must remain readable
  * Tables must enable horizontal scrolling
  * ToC may collapse into a toggleable panel
* Touch interactions must be reliable and forgiving.


#### 6.6 Accessibility

* Sufficient contrast ratios for text and charts.
* Interactive elements must be keyboard-accessible.
* Semantic HTML must be used where applicable:

  * `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
* Charts must include textual summaries or captions that convey key information.

#### 6.7 Performance and Stability

* No unnecessary reflows or repaints.
* Charts must render deterministically and consistently across reloads.
* UI behavior must be:

  * Free of jitter
  * Free of race conditions
* Page load and interaction latency must not interfere with reading or interpretation.


#### 6.8 Professional Restraint

The UI must **never**:

* Use gamification, badges, or novelty effects.
* Employ marketing-style emphasis (e.g., “best”, “fastest”) without data.
* Distract from the data with excessive visual effects.
* Imply conclusions through visual bias rather than explicit analysis.

#### 6.9 UI Quality Acceptance Criteria

The UI is considered acceptable only if:

* A JVM performance engineer can navigate, interpret, and critique the report without confusion.
* Visual elements reinforce—not replace—analytical reasoning.
* No design choice materially biases interpretation of results.

## Report Spec

Structure:
- Introduction & Summary
- System Under Test
- Methodology
- Results
- Conclusions
- Reproducibility
- References

### Introduction & Summary

- Purpose of the benchmark
- Scope and limitations
- High-level summary of key findings
- Intended audience (engineers, JVM practitioners, researchers)

### System Under Test

JVM & Execution Environment
- JVM implementation (e.g., OpenJDK HotSpot)
- JVM version and vendor
- Garbage collector used (G1, ZGC, Shenandoah, Serial)
- Heap configuration (-Xms, -Xmx)
- JIT compilation status (tiered compilation assumed unless stated)

Hardware Model
- CPU:
  * Architecture
  * Core count
  * Cache hierarchy
- Memory:
  * UMA vs NUMA
  * Total capacity
- Storage:
  * SSD/HDD (only if persistence is tested)
- OS:
  * Kernel version
  * Scheduler behavior

### Methodology

-  Workload Design
	- Data Specification
 		- Data Types
   		- Cardinality:
 	- Metrics: Latency(Mean, P90 and P99),
  	- Workload:
   		- Simple: Read; Write, Delete.
     	- Compose: Read-heavy (e.g., 95% lookup), Write-heavy (e.g., 70% insert/remove), Balanced.
-  Execution Condition(s)
	- Warm-up strategy (iterations, time-based)
 	- Measurement phase duration
  	- Fork count / process isolation
   	- CPU pinning or affinity (if used)
   	- Background noise controls
-  Threats to Validity
	- JIT warm-up effects
	- GC pauses and heap resizing
	- CPU frequency scaling and OS noise
 	- CPU frequency scaling
  	- OS scheduler noise
   	- Measurement observer effects

### Results

> Results are presented using a tab-based interface, where each tab corresponds to a distinct performance analysis dimension (e.g., throughput, latency, memory footprint, scalability). Each tab contains the relevant charts, tables, and key findings for that dimension.

Each tab must include:

- Charts
- Tables
- Interpretive text (no raw dumps)

Statistical Integrity
- Confidence intervals
- Outlier identification and handling
- Downloadable raw datasets (CSV/JSON)
- Explicit statement of sample size

Tabs:
- Overview
- Time
	- Throughput
	- Latency
- Space
	- Memory footprint
- Scaling
	- Throughput vs Workload

### Conclusions

- Comparative analysis by:
	- Workload
	- Data structure
- Strengths and weaknesses of each collection
- Practical guidance for engineers
- Summary table of findings

### Reproducibility

- Explicit reproduction instructions
- JVM flags and invocation commands
- Dataset download links
- Versioning and determinism notes

## References

- Bloch, J. (2018). Effective Java (3rd ed.). Addison-Wesley.
- Oracle. (2023). Java Collections Framework Overview. Oracle Docs.
- Shipilev, A. (2016). Java Microbenchmark Harness (JMH). OpenJDK.
- Click, C. (2014). Java Performance: The Definitive Guide. O'Reilly Media.
- Lea, D. (2020). Concurrent Programming in Java (2nd ed.). Addison-Wesley.
