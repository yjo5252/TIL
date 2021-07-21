# NVIDIA Nsight Compute 
### Nsight compute 
* an interactive kernel profiler for CUDA applications 
* 기능 (feature): 
    * provides detailed `performance metrics` 
        * metric collection is customizable and data-driven 
    * `API debugging`
    * via a `user interface` and `command line` tool 
        * user interface is customizable and data-driven
    * allow users to compare results within the tool 
    * extended with `anaylsis scripts` for post-processing results.


### Roofline Analysis 
* Roofline : a visual representation memory and compute capacities of your system.
* analysis pinpoints 
    * your achieved arithmetic intensity **FLOP performance** with respect to these limitations. 
* this visualizatin guides the direction and value of optimizatin efforts

### Memory Workload Analysis 
* Visualize **Memory throughput** on the profiled platform and follow guided analysis for improving performance. 
* For NVIDIA Ampere and later architectures
    * Compute Data Compression throughput and ratio, to ensure data is compacted for **maximum performance**. 
    * Asynchronous Copy metrics, validates the most direct route to shared memory. 
* Set multiple baselines to compare variations in GPU architecture, kernel launch parameters, memory usage. 
* Compare **performance metrics(성능 측정항목)** between baselines and the current run, including the ability to compare child process. 

### Run from Nsight Compute GUI or from Console Command Line
* Nsight Compute GUI provides text for console commands 
* GUI/Console provides similar features(tools), functionality(how features work), output, and reports

### CUDA Task Graph Profiling 
* Stop at a kernel launch from a graph node
* State of graph node shown in resource page 
* Export graph visualization 

### Source Code Correlation 소스코드 상관관계
* Correlate invidual Source, SASS, or PTX lines and metrics 
* Shown here with PC Sampling data available in Volta and Turing architecures 
* Heat map for identifying high metirc values


### Features 
* Interactive kernel profiler
* Profiler report for kernels and/or child process



* kernel 
