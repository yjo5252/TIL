# nsight system 
* 설치 도큐먼트 필사 
## installation guide - NVIDIA Nsight system installation guide


* nsight system is a statistical sampling profiler with tracing features 
* it is desgined to work with devices and devkits based on NVIDIA Tegra SoCs (system-on-chip), ARM SBSA (server based system architecture) systems, IBM Power systems, and systems based on the x86_64 processor architecture that also include NVIDIA GPUs) 

### Overview 
* refer to the **device** on which profiling happens as the **target**, and the **computer** on which the user works and controls the profiling session as the **host**. 
* note that x86_64 based system is on the same device
* whereas Tegra, ARM, or IBM Power based systems are always seperate. 

Three different activities are distinguished as follows: 
* Profiling - The process of collecting any performance data. A profiling session in Nsight systems typically includes <b>sampling and tracing</b>. 
* Sampling - The process of periodically stopping the profilee (the application under investigation during the profiling session), typically to collect backtraces (call stacks of active threads), which allows you to understand statistically how much time is spent in each function. Additionally, hardware counters can also be sampled. This process is inherently imprecise when a low number of samples have been collected
* Tracing - The process of collecting precise information about various activities happening in the profile in the system. For example profile API execution may be traced providing the exact time and duration of a function call. 

General facts
* supports - multiple generations of Tegra SoCs,NVIDIA discrete GPUs, and various CPU architectures, as well as various target and host operating systems.
*  This documentation describes the full set of features available in any version of Nsight Systems. In the event that a feature is not available in all versions, that will be noted in the text. 
* In general, Nsight systems embedded platforms edition indicate the package that supports tegra processors for the embedded and automotive market and Nsight systems workstation edition supports x86_564, IBM Power, and ARM server (SBSA) processor for the workstation and cluster market. 

Common features that are supported by Nsight Systems on most platforms include the following: 

* Sampling of the profilee and collecting backtraces using multiple algorithms (such as frame pointer of DWARF data).
* Building top-down, bottom-up, and flat views as appropriate. This information helps identify performance bottlenecks in CPU-intensive code. 
* Sampling or tracing system power behaviors, such as CPU frequency. 
* (Only on Nsight Systems Embedded Platforms Edition) Sampling counters from ARM PMU (Performance Monitoring Unit). Information such as cache misses gets statistically correlated with function execution.
* Support for multiple windows. Users with multiple monitors can see multiple reports simultaneously, or have multiple view into the same report file. 


With a Nsight systems. 

a user could do the followings 

1. identify call paths that monopolize the CPU 
2. identify individual functions that monopolize the CPU (across different call pahts) 
3. For nsight systems, embedded platforms edition, identify functions that have poor cache utilization 
4. if platform supports CUDA, see visual representation of CUDA Runtime and Drvier API calls, as well as CUDA GPU workload. Nsight Systems uses the CUDA Profiling Tools Interface (CUPTI) for more information, 
5. If the user annotates with NVIDIA Tools Extension (NVTX), see visual representation of NVTX annotations: ranges, markers, and thread names. 
6. For windows targets, see visual representation of D3D12: which API calls are being made on the CPU, graphic frames, stutter analysis, as well as Vulkan GPU workloads (command buffers and debug ranges) 

## System Requirements 

Nsight systems supports multiple Platforms. 

### Setting up the CLI 
* All Nsight Systems targets can be profiled using the CLI 
* The CLI is especially helpful when scripts are used to run unattended collections or when access to the target system via ssh is not possible. this can be used to enable collection in a Docker contaier. 
