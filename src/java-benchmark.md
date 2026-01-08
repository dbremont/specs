Generate a web site - for the presentation of the Following Becnhmark 

- Web Site Technical Featutes

- Vanilla HTML,
- Use Tailwind CSS
- Use Apache ECharts

Benchmark Spec:

I Need to Design and Conduct a Benchmark on Java Standard Library Collections  (ArrayList, LinkedList, Collections.synchronizedList(new ArrayList<>());)  :

- Introduction & Summary
- System Under Test (SUT)
**Specification Environment**
	- JVM implementation (e.g., OpenJDK HotSpot)
	- JVM version and vendor
	- Garbage Collector (G1, ZGC, Shenandoah, Serial)
	- Heap sizing strategy (`Xms`, `Xmx`)
	- JIT compilation enabled (default tiered compilation)

**Hardware Model**

	- CPU architecture (cores, cache hierarchy)
	- Memory (NUMA vs UMA)
	- Storage (SSD/HDD only relevant for persistence tests)
	- OS scheduler and kernel version


- Methodology

**Threats to Validity**

- JIT warm-up effects
- GC pauses and heap resizing
- CPU frequency scaling and OS noise

Workload Design

**Operation Mix**

- Primitive operations:
    - Insert (`add`, `put`)
    - Lookup (`get`, `contains`)
    - Update (`set`, overwrite)
    - Remove (`remove`)
    - Iteration (sequential traversal)
- Composite workloads:
    - Read-heavy (e.g., 95% lookup)
    - Write-heavy (e.g., 70% insert/remove)
    - Balanced mixes

**Data Characteristics**

- Key/value types:
    - Primitive wrappers (`Integer`, `Long`)
    - Strings (short vs long)
    - Custom objects with varying `hashCode()` quality
- Cardinality:
    - Small (10²), medium (10⁴), large (10⁶+)
- Distribution:
    - Uniform
    - Skewed (Zipfian, hotspot keys)
    - Adversarial (hash collisions)

**Temporal Structure**

- Warm-up phase (to stabilize JIT)
- Measurement phase
- Cool-down / teardown

**Concurrency Model (if applicable)**

- Thread count scaling
- Read/write contention ratios
- Lock-free vs lock-based behavior

**Performance Metrics**:

- Throughput (ops/sec)
- Latency:
    - Mean
    - Percentiles (P90, P99)
- Memory footprint (bytes per element)


- Results Presentation  (Generate a presentation of synthethic results - make sure to generate a sort of tab based horizontal presentation for this results)
	- Analysis Dimenions: Workload; -> Results; Key Findings
	- Dimensions: Time (Throughput; Latency); Space; Throughput Scaling with Data Size, Others (GC, ...), ...

- Conclusions

	- Generate a comparison; workload; data structure; 
	- Geneary a Summary of the Findings

- References


