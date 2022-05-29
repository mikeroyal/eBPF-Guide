<h1 align="center">
 <img src="https://user-images.githubusercontent.com/45159366/145732233-75bd4258-e436-404d-a707-4dca9a1d5beb.png">
  <br />
 eBPF Guide
</h1>

#### A guide covering eBPF including the applications, libraries and tools that will make you a better and more efficient eBPF development.

**Note: You can easily convert this markdown file to a PDF in [VSCode](https://code.visualstudio.com/) using this handy extension [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf).**

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/145732234-12f0e79f-d268-422e-b402-b2dc9feeab51.png">
  <br />
</p>

# Table of Contents

1. [Getting Started with eBPF](https://github.com/mikeroyal/eBPF-Guide#getting-started-with-eBPF)
   
     - [eBPF Tools & Libraries](https://github.com/mikeroyal/eBPF-Guide#ebpf-tools--libraries)
     - [Books & Tutorials](https://github.com/mikeroyal/eBPF-Guide#books--tutorials)

2. [LLVM Development](https://github.com/mikeroyal/eBPF-Guide#llvm-development)

3. [GO Development](https://github.com/mikeroyal/eBPF-Guide#go-development)

4. [C++ Development](https://github.com/mikeroyal/eBPF-Guide#cc-development)

5. [Rust Development](https://github.com/mikeroyal/eBPF-Guide#rust-development)

6. [Networking](https://github.com/mikeroyal/eBPF-Guide#networking)

7. [Kubernetes](https://github.com/mikeroyal/eBPF-Guide#kubernetes)

8. [Databases](https://github.com/mikeroyal/eBPF-Guide#databases)


# Getting Started with eBPF
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

## eBPF Tools & Libraries

[eBPF](https://ebpf.io/) is a technology that can run sandboxed programs in the Linux kernel without changing kernel source code or loading kernel modules. By making the Linux kernel programmable, infrastructure software can leverage existing layers, making them more intelligent and feature-rich without continuing to add additional layers of complexity to the system.

[eBPF for Windows](https://github.com/microsoft/ebpf-for-windows) is an eBPF implementation that runs on top of Windows. eBPF is a well-known technology for providing programmability and agility, especially for extending an OS kernel, for use cases such as DoS protection and observability. [Cilium L4 Load Balancer using eBPF-for-Windows](https://github.com/microsoft/ebpf-for-windows-demo/blob/main/cilium/load_balancer/docs/CiliumL4LBSetup.md)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/145732237-9906cb94-41fb-4302-b1bf-b4584975534b.png">
  <br />
</p>

**eBPF Architecture Overview. Credit: [eBPF.io](https://ebpf.io/)**

[XDP(eXpress Data Path)](https://www.tigera.io/learn/guides/ebpf/) is a technology that allows developers to attach eBPF programs to low-level hooks, implemented by network device drivers in the Linux kernel(since version 4.8), as well as generic hooks that run after the device driver. XDP can be used to achieve high-performance packet processing in an eBPF architecture, primarily using kernel bypass. 

[AF_XDP](https://01.org/linuxgraphics/gfx-docs/drm/networking/af_xdp.html) is an address family that is optimized for high performance packet processing.

[BPF Compiler Collection (BCC)](https://github.com/iovisor/bcc) is a toolkit for creating efficient kernel tracing and manipulation programs, and includes several useful tools and examples. It makes use of extended BPF (Berkeley Packet Filters), formally known as eBPF, a new feature that was first added to Linux 3.15. Though, much of what BCC uses requires Linux 4.1 and above.

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/170851575-c767bb1a-74e3-47e0-bd08-59291eca7dd6.png">
  <br />
</p>

**BCC performance tools. Credit: [Brendan Gregg](https://github.com/iovisor/bcc/blob/master/images/bcc_tracing_tools_2019.png)**

[Bpftrace](https://github.com/iovisor/bpftrace) is a high-level tracing language for Linux eBPF. Its language is inspired by awk and C, and predecessor tracers such as DTrace and SystemTap. bpftrace uses LLVM as a backend to compile scripts to eBPF bytecode and makes use of BCC as a library for interacting with the Linux eBPF subsystem as well as existing Linux tracing capabilities and attachment points.

[Cilium](https://github.com/cilium/cilium) is an open source project that provides eBPF-powered networking, security and observability. It has been specifically designed from the ground up to bring the advantages of eBPF to the world of Kubernetes and to address the new scalability, security and visibility requirements of container workloads.

[Falco](https://github.com/falcosecurity/falco) is a behavioral activity monitor designed to detect anomalous activity in applications. Falco audits a system at the Linux kernel layer with the help of eBPF. It enriches gathered data with other input streams such as container runtime metrics and Kubernetes metrics, and allows to continuously monitor and detect container, application, host, and network activity.

[Katran](https://github.com/facebookincubator/katran) is a C++ library and eBPF program to build a high-performance layer 4 load balancing forwarding plane. Katran leverages the XDP infrastructure from the Linux kernel to provide an in-kernel facility for fast packet processing. Its performance scales linearly with the number of NIC's receive queues and it uses RSS friendly encapsulation for forwarding to L7 load balancers.

[Hubble](https://github.com/cilium/hubble) is a fully distributed networking and security observability platform for cloud native workloads. It is built on top of Cilium and eBPF to enable deep visibility into the communication and behavior of services as well as the networking infrastructure in a completely transparent manner.

[Pixie](https://docs.pixielabs.ai/) is an open-source observability tool for Kubernetes applications. It's used to view the high-level state of your cluster (service maps, cluster resources, application traffic) and also drill down into more detailed views (pod state, flame graphs, individual full-body application requests).

[Kubectl-trace](https://github.com/iovisor/kubectl-trace) is a kubectl plugin that allows for scheduling the execution of bpftrace(8) programs in Kubernetes clusters. kubectl-trace does not require installation of any components directly onto a Kubernetes cluster in order to execute bpftrace programs. When pointed to a cluster, it schedules a temporary job called trace-runner that executes bpftrace.

[Ply](https://github.com/iovisor/ply) is a dynamic tracer for Linux which is built upon eBPF. It has been designed with embedded systems in mind, is written in C and all that ply needs to run is libc and a modern Linux kernel with eBPF support, meaning, it does not depend on LLVM for its program generation. It has a C-like syntax for writing scripts and is heavily inspired by awk(1) and dtrace(1).

[Tracee](https://github.com/aquasecurity/tracee) is a Runtime Security and forensics tool for Linux. It is using Linux eBPF technology to trace your system and applications at runtime, and analyze collected events to detect suspicious behavioral patterns.

[bpfcov](https://github.com/elastic/bpfcov) is a source-code based coverage for eBPF programs actually running in the Linux kernel.

[eCapture](https://github.com/ehids/ecapture) is a tool that captures SSL/TLS text content without CA cert using eBPF.  

[Tetragon](https://github.com/cilium/tetragon) is a eBPF-based Security Observability and Runtime Enforcement.
 
[SkyWalking](https://github.com/apache/skywalking) is an open source APM system, including monitoring, tracing, diagnosing capabilities for distributed system in Cloud Native architecture. 

[Skydive](https://github.com/skydive-project/skydive) is an open source real-time network topology and protocols analyzer. It aims to provide a comprehensive way of understanding what is happening in the network infrastructure.

The [Linux kernel](https://www.kernel.org/) contains the eBPF runtime required to run eBPF programs. It implements the bpf(2) system call for interacting with programs, maps, BTF and various attachment points where eBPF programs can be executed from. The kernel contains a eBPF verifier in order to check programs for safety and a JIT compiler to translate programs to native machine code. User space tooling such as bpftool and libbpf are also maintained as part of the upstream kernel.

[Landlock LSM(Linux Security Module)](https://www.kernel.org/doc/html/latest/security/landlock.html) is a framework to create scoped access-control (sandboxing). Landlock is designed to be usable by unprivileged processes while following the system security policy enforced by other access control mechanisms (DAC, LSM, etc.).

[LLVM compiler](https://llvm.org/) infrastructure contains the eBPF backend required to translate programs written in a C-like syntax to eBPF instructions. LLVM generates eBPF ELF files which contain program code, map descriptions, relocation information and BTF meta data. These ELF files contain all necessary information for eBPF loaders such as libbpf to prepare and load programs into the Linux kernel.

[Gobpf](https://github.com/iovisor/gobpf) is a Go-based library which provides Go bindings for the BCC framework as well as low-level routines to load and use eBPF programs from ELF files.

[rbpf](https://github.com/qmonnet/rbpf) is a Rust virtual machine and JIT compiler for eBPF programs.

[Libbpfgo](https://github.com/aquasecurity/libbpfgo) is a Go wrapper around libbpf. It supports BPF CO-RE and its goal is to be a complete implementation of libbpf APIs. It uses CGo to call into linked versions of libbpf.

[Libbpf](https://github.com/libbpf/libbpf) is a C/C++ based library which is maintained as part of the upstream Linux kernel. It contains an eBPF loader which takes over processing LLVM generated eBPF ELF files for loading into the kernel. libbpf received a major boost in capabilities and sophistication and closed many existing gaps with BCC as a library. It also supports important features not available in BCC such as global variables and BPF skeletons.

[Libbpf-rs](https://github.com/libbpf/libbpf-rs) is a safe, idiomatic, and opinionated wrapper API around libbpf written in Rust. libbpf-rs, together with libbpf-cargo (libbpf cargo plugin) allows to write 'compile once run everywhere' (CO-RE) eBPF programs.

[Redbpf](https://github.com/redsift/redbpf) is a Rust eBPF toolchain that contains a collection of Rust libraries to work with BPF/eBPF programs.

### Books & Tutorials
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

  - [BPF Performance Tools (book) by Brendan Gregg](https://www.brendangregg.com/bpf-performance-tools-book.html). **[GitHub repo](https://github.com/brendangregg/bpf-perf-tools-book) for book**.
 
  - [Systems Performance: Enterprise and the Cloud, 2nd Edition (2020) by Brendan Gregg](https://www.brendangregg.com/systems-performance-2nd-edition-book.html)
 
  - [Security Observability with eBPF by Jed Salazar & Natalia Reka Ivanko](https://www.oreilly.com/library/view/security-observability-with/9781492096719/)
 
  - [What Is eBPF? by Liz Rice](https://www.oreilly.com/library/view/what-is-ebpf/9781492097266/)
  
  - [The Beginner's Guide to eBPF by Liz Rice](https://github.com/lizrice/ebpf-beginners)
 
  - [eBPF - From a Programmer’s Perspective by Niclas Hedam (PDF)](https://hed.am/papers/2021-EBPF.pdf)
 
  - [Learn eBPF Tracing: Tutorial and Examples by Brendan Gregg](https://www.brendangregg.com/blog/2019-01-01/learn-ebpf-tracing.html)
 
  - [eBPF Instruction Set — The Linux Kernel documentation](https://www.kernel.org/doc/html/latest/bpf/instruction-set.html)
 
  - [How We Used eBPF to Build Programmable Packet Filtering in Magic Firewall | Cloudflare](https://blog.cloudflare.com/programmable-packet-filtering-with-magic-firewall/)
 
  - [eBPF assembly with LLVM by Quentin Monnet](https://qmonnet.github.io/whirl-offload/2020/04/12/llvm-ebpf-asm/)

# LLVM Development
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/130368411-816a637d-8ca6-460c-a21d-13c3fbdadb80.png">
  <br />
</p>

## LLVM Learning Resources

[LLVM](https://github.com/llvm/) is a library that has collection of modular/reusable compiler and toolchain  components (assemblers, compilers, and debuggers). With these components LLVM can be used as a compiler framework, providing a front-end(parser and lexer) and a back-end (code that converts LLVM's representation to actual machine code).

[Clang](https://clang.llvm.org/) is a language front-end and tooling infrastructure for languages in the C language family (C, C++, Objective C/C++, OpenCL, CUDA, and RenderScript) for the LLVM project.

[LLVM Project GitHub](https://github.com/llvm/llvm-project//)

[LLVM Documentation](https://llvm.org/docs/index.html)

[LLVM Discussion Forum](https://llvm.discourse.group/)

[LLVM | Apple Developer Forums](https://developer.apple.com/forums/tags/llvm/)

[Contributing to LLVM](https://llvm.org/docs/Contributing.html)

[Getting Started with LLVM](https://llvm.org/docs/GettingStartedTutorials.html)

[Getting Started with Clang](https://clang.llvm.org/get_started.html)

[How To Setup Clang Tooling For LLVM](https://clang.llvm.org/docs/HowToSetupToolingForLLVM.html)

[Using Clang-Tidy in Visual Studio](https://docs.microsoft.com/en-us/cpp/code-quality/clang-tidy)

[Configure VS Code for Clang/LLVM on macOS](https://code.visualstudio.com/docs/cpp/config-clang-mac)

## LLVM Tools, Libraries and Frameworks

[Visual Studio Code](https://code.visualstudio.com/) is a code editor redefined and optimized for building and debugging modern web and cloud applications.

[Code Server](https://coder.com/) is a tool that allows you to run [VS Code](https://code.visualstudio.com/) on any machine anywhere and access it in the browser.

[Clang-Format](https://marketplace.visualstudio.com/items?itemName=xaver.clang-format) is a tool to format C/C++/Java/JavaScript/Objective-C/Objective-C++/Protobuf code.

[Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) is a clang-based C++ "linter" tool. Its purpose is to provide an extensible framework for diagnosing and fixing typical programming errors, like style violations, interface misuse, or bugs that can be deduced via static analysis. clang-tidy is modular and provides a convenient interface for writing new checks.

[Clangd](https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd) is a Visual Studio Code extension that provides C/C++ language IDE features for VS Code using [clangd](https://clangd.llvm.org/).

[LLD](https://lld.llvm.org/) is a linker from the LLVM project that is a drop-in replacement for system linkers and runs much faster than them. It also provides features that are useful for toolchain developers. The linker supports ELF (Unix), PE/COFF (Windows), Mach-O (macOS) and WebAssembly in descending order.

[TinyGo](https://tinygo.org/) is a Go compiler(based on LLVM) intended for use in small places such as microcontrollers, WebAssembly (Wasm), and command-line tools.

[FileCheck](https://llvm.org/docs/CommandGuide/FileCheck.html) is a flexible pattern matching file verifier.

[tblgen](https://llvm.org/docs/CommandGuide/tblgen.html) is a description to C++ Code.

[clang-tblgen](https://llvm.org/docs/CommandGuide/clang-tblgen.html) is a description to C++ Code for Clang.

[lldb-tblgen](https://llvm.org/docs/CommandGuide/lldb-tblgen.html) is a description to C++ Code for LLDB.

[llvm-tblgen](https://llvm.org/docs/CommandGuide/llvm-tblgen.html) is a target description to C++ Code for LLVM.

[mlir-tblgen](https://llvm.org/docs/CommandGuide/mlir-tblgen.html) is a description to C++ Code for MLIR.

[lit](https://llvm.org/docs/CommandGuide/lit.html) is a LLVM Integrated Tester.

[llvm-exegesis](https://llvm.org/docs/CommandGuide/llvm-exegesis.html) is a LLVM Machine Instruction Benchmark.

[llvm-locstats](https://llvm.org/docs/CommandGuide/llvm-locstats.html) is a calculate statistics on DWARF debug location.

[llvm-pdbutil](https://llvm.org/docs/CommandGuide/llvm-pdbutil.html) is a PDB File forensics and diagnostics.

[llvm-profgen](https://llvm.org/docs/CommandGuide/llvm-profgen.html) is a LLVM SPGO profile generation tool

[bugpoint](https://llvm.org/docs/CommandGuide/bugpoint.html) is a automatic test case reduction tool.

[llvm-extract](https://llvm.org/docs/CommandGuide/llvm-extract.html) is a extract a function from an LLVM module.

[llvm-bcanalyzer](https://llvm.org/docs/CommandGuide/llvm-bcanalyzer.html) is a LLVM bitcode analyzer.

[llvm-addr2line](https://llvm.org/docs/CommandGuide/llvm-addr2line.html) is a drop-in replacement for addr2line.

[llvm-ar](https://llvm.org/docs/CommandGuide/llvm-ar.html) is a  LLVM archiver.

[llvm-cxxfilt](https://llvm.org/docs/CommandGuide/llvm-cxxfilt.html) is a  LLVM symbol name demangler.

[llvm-install-name-tool](https://llvm.org/docs/CommandGuide/llvm-install-name-tool.html) is a LLVM tool for manipulating install-names and rpaths.

[llvm-nm](https://llvm.org/docs/CommandGuide/llvm-nm.html) is a list LLVM bitcode and object file’s symbol table.

[llvm-objcopy](https://llvm.org/docs/CommandGuide/llvm-objcopy.html) is a  object copying and editing tool.

[llvm-objdump](https://llvm.org/docs/CommandGuide/llvm-objdump.html) is a  LLVM’s object file dumper.

[llvm-ranlib](https://llvm.org/docs/CommandGuide/llvm-ranlib.html) is a  generates an archive index.

[llvm-readelf](https://llvm.org/docs/CommandGuide/llvm-readelf.html) is a  GNU-style LLVM Object Reader.

[llvm-size](https://llvm.org/docs/CommandGuide/llvm-size.html) is a  print size information.

[llvm-strings](https://llvm.org/docs/CommandGuide/llvm-strings.html) is a  print strings.

[llvm-strip](https://llvm.org/docs/CommandGuide/llvm-strip.html) is a  object stripping tool.

# GO Development
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/93719679-068f8c80-fb39-11ea-8baa-9e779ee58a0a.png">
  <br />
</p>

## Go Learning Resources

[Go](https://golang.org/) is an open source programming language that makes it easy to build simple, reliable, and efficient software.

[Golang Contribution Guide](https://golang.org/doc/contribute.html)

[Google Developers Training](https://developers.google.com/training/)

[Google Developers Certification](https://developers.google.com/certification/)

[Uber's Go Style Guide](https://github.com/uber-go/guide/blob/master/style.md)

[GitLab's Go standards and style guidelines](https://docs.gitlab.com/ee/development/go_guide/)

[Effective Go](https://golang.org/doc/effective_go.html)

[Go: The Complete Developer's Guide (Golang) on Udemy](https://www.udemy.com/course/go-the-complete-developers-guide/)

[Getting Started with Go on Coursera](https://www.coursera.org/learn/golang-getting-started)

[Programming with Google Go on Coursera](https://www.coursera.org/specializations/google-golang)

[Learning Go Fundamentals on Pluralsight](https://www.pluralsight.com/courses/go-fundamentals)

[Learning Go on Codecademy](https://www.codecademy.com/learn/learn-go)

## Go Tools and Frameworks

[golang tools](https://pkg.go.dev/golang.org/x/tools) holds the source for various packages and tools that support the Go programming language.

[Go in Visual Studio Code](https://code.visualstudio.com/docs/languages/go) is an extension that gives you language features like IntelliSense, code navigation, symbol search, bracket matching, snippets, and many more that will help you in Golang development.

[Traefik](https://github.com/traefik/traefik) is a modern HTTP reverse proxy and load balancer that makes deploying microservices easy. Traefik integrates with your existing infrastructure components (Docker, Swarm mode, Kubernetes, Marathon, Consul, Etcd, Rancher, Amazon ECS, etc.) and configures itself automatically and dynamically. Pointing Traefik at your orchestrator should be the only configuration step you need.

[Gitea](https://github.com/go-gitea/gitea) is Git with a cup of tea, painless self-hosted git service. Using Go, this can be done with an independent binary distribution across all platforms which Go supports, including Linux, macOS, and Windows on x86, amd64, ARM and PowerPC architectures.

[OpenFaaS](https://github.com/openfaas/faas) is Serverless Functions Made Simple. It makes it easy for developers to deploy event-driven functions and microservices to Kubernetes without repetitive, boiler-plate coding. Package your code or an existing binary in a Docker image to get a highly scalable endpoint with auto-scaling and metrics.

[micro](https://github.com/zyedidia/micro) is a terminal-based text editor that aims to be easy to use and intuitive, while also taking advantage of the capabilities of modern terminals. As its name indicates, micro aims to be somewhat of a successor to the nano editor by being easy to install and use. It strives to be enjoyable as a full-time editor for people who prefer to work in a terminal, or those who regularly edit files over SSH.

[Gravitational Teleport](https://github.com/gravitational/teleport) is a modern security gateway for remotely accessing into Clusters of Linux servers via SSH or SSH-over-HTTPS in a browser or Kubernetes clusters.

[NATS](https://nats.io/) is a simple, secure and performant communications system for digital systems, services and devices. NATS is part of the Cloud Native Computing Foundation (CNCF). NATS has over 30 client language implementations, and its server can run on-premise, in the cloud, at the edge, and even on a Raspberry Pi. NATS can secure and simplify design and operation of modern distributed systems.

[Act](https://github.com/nektos/act) is a GO program that allows you to run our GitHub Actions locally.

[Fiber](https://gofiber.io/) is an [Express](https://github.com/expressjs/express) inspired web framework built on top of [Fasthttp](https://github.com/valyala/fasthttp), the fastest HTTP engine for Go. Designed to ease things up for fast development with zero memory allocation and performance in mind.

[Glide](https://github.com/Masterminds/glide) is a vendor Package Management for Golang.

[BadgerDB](https://github.com/dgraph-io/badger) is an embeddable, persistent and fast key-value (KV) database written in pure Go. It is the underlying database for [Dgraph](https://dgraph.io/), a fast, distributed graph database. It's meant to be a performant alternative to non-Go-based key-value stores like RocksDB.

[Go kit](https://github.com/go-kit/kit) is a programming toolkit for building microservices (or elegant monoliths) in Go. We solve common problems in distributed systems and application architecture so you can focus on delivering business value.

[Codis](https://github.com/CodisLabs/codis) is a proxy based high performance Redis cluster solution written in Go.

[zap](https://github.com/uber-go/zap) is a blazing fast, structured, leveled logging in Go.

[HttpRouter](https://github.com/julienschmidt/httprouter) is a lightweight high performance HTTP request router (also called multiplexer or just mux for short) for Go.

[Gorilla WebSocket](https://github.com/gorilla/websocket) is a Go implementation of the WebSocket protocol.

[Delve](https://github.com/go-delve/delve) is a debugger for the Go programming language.

[GORM](https://github.com/go-gorm/gorm) is a fantastic ORM library for Golang, aims to be developer friendly.

[Go Patterns](https://github.com/tmrts/go-patterns) is a curated collection of idiomatic design & application patterns for Go language.

# C/C++ Development
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/115297894-961e0d80-a111-11eb-81c3-e2bd2ac9a7cd.png">
  <br />
</p>

## C/C++ Learning Resources

[C++](https://www.cplusplus.com/doc/tutorial/) is a cross-platform language that can be used to build high-performance applications developed by Bjarne Stroustrup, as an extension to the C language.

[C](https://www.iso.org/standard/74528.html) is a general-purpose, high-level language that was originally developed by Dennis M. Ritchie to develop the UNIX operating system at Bell Labs. It supports structured programming, lexical variable scope, and recursion, with a static type system. C also provides constructs that map efficiently to typical machine instructions, which makes it one was of the most widely used programming languages today.

[Embedded C](https://en.wikipedia.org/wiki/Embedded_C) is a set of language extensions for the C programming language by the [C Standards Committee](https://isocpp.org/std/the-committee) to address issues that exist between C extensions for different [embedded systems](https://en.wikipedia.org/wiki/Embedded_system). The extensions hep enhance microprocessor features such as fixed-point arithmetic, multiple distinct memory banks, and basic I/O operations. This makes Embedded C the most popular embedded software language in the world.

[C & C++ Developer Tools from JetBrains](https://www.jetbrains.com/cpp/)

[Open source C++ libraries on cppreference.com](https://en.cppreference.com/w/cpp/links/libs)

[C++ Graphics libraries](https://cpp.libhunt.com/libs/graphics)

[C++ Libraries in MATLAB](https://www.mathworks.com/help/matlab/call-cpp-library-functions.html)

[C++ Tools and Libraries Articles](https://www.cplusplus.com/articles/tools/)

[Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)

[Introduction C++ Education course on Google Developers](https://developers.google.com/edu/c++/)

[C++ style guide for Fuchsia](https://fuchsia.dev/fuchsia-src/development/languages/c-cpp/cpp-style)

[C and C++ Coding Style Guide by OpenTitan](https://docs.opentitan.org/doc/rm/c_cpp_coding_style/)

[Chromium C++ Style Guide](https://chromium.googlesource.com/chromium/src/+/master/styleguide/c++/c++.md)

[C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)

[C++ Style Guide for ROS](http://wiki.ros.org/CppStyleGuide)

[Learn C++](https://www.learncpp.com/)

[Learn C : An Interactive C Tutorial](https://www.learn-c.org/)

[C++ Institute](https://cppinstitute.org/free-c-and-c-courses)

[C++ Online Training Courses on LinkedIn Learning](https://www.linkedin.com/learning/topics/c-plus-plus)

[C++ Tutorials on W3Schools](https://www.w3schools.com/cpp/default.asp)

[Learn C Programming Online Courses on edX](https://www.edx.org/learn/c-programming)

[Learn C++ with Online Courses on edX](https://www.edx.org/learn/c-plus-plus)

[Learn C++ on Codecademy](https://www.codecademy.com/learn/learn-c-plus-plus)

[Coding for Everyone: C and C++ course on Coursera](https://www.coursera.org/specializations/coding-for-everyone)

[C++ For C Programmers on Coursera](https://www.coursera.org/learn/c-plus-plus-a)

[Top C Courses on Coursera](https://www.coursera.org/courses?query=c%20programming)

[C++ Online Courses on Udemy](https://www.udemy.com/topic/c-plus-plus/)

[Top C Courses on Udemy](https://www.udemy.com/topic/c-programming/)

[Basics of Embedded C Programming for Beginners on Udemy](https://www.udemy.com/course/embedded-c-programming-for-embedded-systems/)

[C++ For Programmers Course on Udacity](https://www.udacity.com/course/c-for-programmers--ud210)

[C++ Fundamentals Course on Pluralsight](https://www.pluralsight.com/courses/learn-program-cplusplus)

[Introduction to C++ on MIT Free Online Course Materials](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-096-introduction-to-c-january-iap-2011/)

[Introduction to C++ for Programmers | Harvard ](https://online-learning.harvard.edu/course/introduction-c-programmers)

[Online C Courses | Harvard University](https://online-learning.harvard.edu/subject/c)


## C/C++ Tools and Frameworks

[AWS SDK for C++](https://aws.amazon.com/sdk-for-cpp/)

[Azure SDK for C++](https://github.com/Azure/azure-sdk-for-cpp)

[Azure SDK for C](https://github.com/Azure/azure-sdk-for-c)

[C++ Client Libraries for Google Cloud Services](https://github.com/googleapis/google-cloud-cpp)

[Visual Studio](https://visualstudio.microsoft.com/) is an integrated development environment (IDE) from Microsoft; which is a feature-rich application that can be used for many aspects of software development. Visual Studio makes it easy to edit, debug, build, and publish your app. By using Microsoft software development platforms such as Windows API, Windows Forms, Windows Presentation Foundation, and Windows Store.

[Visual Studio Code](https://code.visualstudio.com/) is a code editor redefined and optimized for building and debugging modern web and cloud applications.

[Vcpkg](https://github.com/microsoft/vcpkg) is a C++ Library Manager for Windows, Linux, and MacOS.

[ReSharper C++](https://www.jetbrains.com/resharper-cpp/features/) is a Visual Studio Extension for C++ developers developed by JetBrains.

[AppCode](https://www.jetbrains.com/objc/) is constantly monitoring the quality of your code. It warns you of errors and smells and suggests quick-fixes to resolve them automatically. AppCode provides lots of code inspections for Objective-C, Swift, C/C++, and a number of code inspections for other supported languages. All code inspections are run on the fly.

[CLion](https://www.jetbrains.com/clion/features/) is a cross-platform IDE for C and C++ developers developed by JetBrains.

[Code::Blocks](https://www.codeblocks.org/) is a free C/C++ and Fortran IDE built to meet the most demanding needs of its users. It is designed to be very extensible and fully configurable. Built around a plugin framework, Code::Blocks can be extended with plugins.

[CppSharp](https://github.com/mono/CppSharp) is a tool and set of libraries which facilitates the usage of native C/C++ code with the .NET ecosystem. It consumes C/C++ header and library files and generates the necessary glue code to surface the native API as a managed API. Such an API can be used to consume an existing native library in your managed code or add managed scripting support to a native codebase.

[Conan](https://conan.io/) is an Open Source Package Manager for C++ development and dependency management into the 21st century and on par with the other development ecosystems.

[High Performance Computing (HPC) SDK](https://developer.nvidia.com/hpc) is a comprehensive toolbox for GPU accelerating HPC modeling and simulation applications. It includes the C, C++, and Fortran compilers, libraries, and analysis tools necessary for developing HPC applications on the NVIDIA platform.

[Thrust](https://github.com/NVIDIA/thrust) is a C++ parallel programming library which resembles the C++ Standard Library. Thrust's high-level interface greatly enhances programmer productivity while enabling performance portability between GPUs and multicore CPUs. Interoperability with established technologies such as CUDA, TBB, and OpenMP integrates with existing software.

[Boost](https://www.boost.org/) is an educational opportunity focused on cutting-edge C++. Boost has been a participant in the annual Google Summer of Code since 2007, in which students develop their skills by working on Boost Library development.

[Automake](https://www.gnu.org/software/automake/) is a tool for automatically generating Makefile.in files compliant with the GNU Coding Standards. Automake requires the use of GNU Autoconf.

[Cmake](https://cmake.org/) is an open-source, cross-platform family of tools designed to build, test and package software. CMake is used to control the software compilation process using simple platform and compiler independent configuration files, and generate native makefiles and workspaces that can be used in the compiler environment of your choice.

[GDB](http://www.gnu.org/software/gdb/) is a debugger, that allows you to see what is going on `inside' another program while it executes or what another program was doing at the moment it crashed.

[GCC](https://gcc.gnu.org/) is a compiler Collection that includes front ends for C, C++, Objective-C, Fortran, Ada, Go, and D, as well as libraries for these languages.

[GSL](https://www.gnu.org/software/gsl/) is a numerical library for C and C++ programmers. It is free software under the GNU General Public License. The library provides a wide range of mathematical routines such as random number generators, special functions and least-squares fitting. There are over 1000 functions in total with an extensive test suite.

[OpenGL Extension Wrangler Library (GLEW)](https://www.opengl.org/sdk/libs/GLEW/) is a cross-platform open-source C/C++ extension loading library. GLEW provides efficient run-time mechanisms for determining which OpenGL extensions are supported on the target platform.

[Libtool](https://www.gnu.org/software/libtool/) is a generic library support script that hides the complexity of using shared libraries behind a consistent, portable interface. To use Libtool, add the new generic library building commands to your Makefile, Makefile.in, or Makefile.am.

[Maven](https://maven.apache.org/) is a software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation from a central piece of information.

[TAU (Tuning And Analysis Utilities)](http://www.cs.uoregon.edu/research/tau/home.php) is capable of gathering performance information through instrumentation of functions, methods, basic blocks, and statements as well as event-based sampling. All C++ language features are supported including templates and namespaces.

[Clang](https://clang.llvm.org/) is a production quality C, Objective-C, C++ and Objective-C++ compiler when targeting X86-32, X86-64, and ARM (other targets may have caveats, but are usually easy to fix). Clang is used in production to build performance-critical software like Google Chrome or Firefox.

[OpenCV](https://opencv.org/) is a highly optimized library with focus on real-time applications. Cross-Platform C++, Python and Java interfaces support Linux, MacOS, Windows, iOS, and Android.

[Libcu++](https://nvidia.github.io/libcudacxx) is the NVIDIA C++ Standard Library for your entire system. It provides a heterogeneous implementation of the C++ Standard Library that can be used in and between CPU and GPU code.

[ANTLR (ANother Tool for Language Recognition)](https://www.antlr.org/) is a powerful parser generator for reading, processing, executing, or translating structured text or binary files. It's widely used to build languages, tools, and frameworks. From a grammar, ANTLR generates a parser that can build parse trees and also generates a listener interface that makes it easy to respond to the recognition of phrases of interest.

[Oat++](https://oatpp.io/) is a light and powerful C++ web framework for highly scalable and resource-efficient web application. It's zero-dependency and easy-portable.

[JavaCPP](https://github.com/bytedeco/javacpp) is a program that provides efficient access to native C++ inside Java, not unlike the way some C/C++ compilers interact with assembly language.

[Cython](https://cython.org/) is a language that makes writing C extensions for Python as easy as Python itself. Cython is based on Pyrex, but supports more cutting edge functionality and optimizations such as calling C functions and declaring C types on variables and class attributes.

[Spdlog](https://github.com/gabime/spdlog) is a very fast, header-only/compiled, C++ logging library.

[Infer](https://fbinfer.com/) is a static analysis tool for Java, C++, Objective-C, and C. Infer is written in [OCaml](https://ocaml.org/).

# Rust Development
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/119279024-f0613100-bbdd-11eb-9b52-30c276f8cc0f.png">
  <br />
</p>

## Rust Learning Resources

[Rust](https://www.rust-lang.org) is a multi-paradigm programming language focused on performance and safety. Rust has a comparable amount of runtime to C and C++, and has set up its standard library to be amenable towards OS development. Specifically, the standard library is split into two parts: core and std. Core is the lowest-level aspects only, and doesn't include things like allocation, threading, and other higher-level features.

[The Rust Language Reference](https://doc.rust-lang.org/nightly/reference/)

[The Rust Programming Language Book](https://doc.rust-lang.org/book/)

[Learning Rust](https://www.rust-lang.org/learn)

[Why AWS loves Rust](https://aws.amazon.com/blogs/opensource/why-aws-loves-rust-and-how-wed-like-to-help/)

[Rust Programming courses on Udemy](https://www.udemy.com/courses/search/?src=ukw&q=Rust)

[Safety in Systems Programming with Rust at Standford by Ryan Eberhardt](https://reberhardt.com/blog/2020/10/05/designing-a-new-class-at-stanford-safety-in-systems-programming.html)

[WebAssembly meets Kubernetes with Krustlet using Rust](https://cloudblogs.microsoft.com/opensource/2020/04/07/announcing-krustlet-kubernetes-rust-kubelet-webassembly-wasm/)

[Microsoft's Project Verona](https://github.com/microsoft/verona/blob/master/docs/explore.md)

## Rust Tools and Frameworks

[Cargo](https://github.com/rust-lang/cargo) is a package manager that downloads your Rust project’s dependencies and compiles your project.

[Crater](https://crater.rust-lang.org/) is a tool to run experiments across parts of the Rust ecosystem. Its primary purpose is to detect regressions in the Rust compiler, and it does this by building a large number of crates, running their test suites and comparing the results between two versions of the Rust compiler. It can operate locally (with Docker as the only dependency) or distributed on the cloud. It can operate locally (with Docker as the only dependency) or distributed on the cloud.

[VSCode-Rust](https://github.com/rust-lang/vscode-rust) is plugin that adds language support for Rust to Visual Studio Code. Rust support is powered by a separate language server - either by the official Rust Language Server (RLS) or rust-analyzer, depending on the user's preference. If you don't have it installed, the extension will install it for you (with permission). This extension is built and maintained by the Rust IDEs and editors team with the focus on providing a stable, high quality extension that makes the best use of the respective language server.

[Apache Arrow](https://github.com/apache/arrow) is a development platform for in-memory analytics. It contains a set of technologies that enable big data systems to process and move data fast. Arrow's libraries are available for C, C++, C#, Go, Java, JavaScript, MATLAB, Python, R, Ruby, and Rust.

[Wasmer](https://wasmer.io/) enables super lightweight containers based on [WebAssembly](https://webassembly.org/) that can run anywhere such as the Desktop to the Cloud and IoT devices, and also embedded in [any programming language](https://github.com/wasmerio/wasmer#language-integrations).

[Firecracker](https://firecracker-microvm.github.io) is an open source virtualization technology that is purpose-built for creating and managing secure, multi-tenant container and function-based services that provide serverless operational models. Firecracker runs workloads in lightweight virtual machines, called microVMs, which combine the security and isolation properties provided by hardware virtualization technology with the speed and flexibility of containers. Firecracker has also been integrated in container runtimes, for example [Kata Containers](https://github.com/kata-containers/documentation/wiki/Initial-release-of-Kata-Containers-with-Firecracker-support) and [Weaveworks Ignite](https://github.com/weaveworks/ignite).

[Tokio](https://github.com/tokio-rs/tokio) is an event-driven, non-blocking I/O platform for writing asynchronous applications with the Rust programming language.

[TiKV](https://github.com/tikv/tikv) is an open-source distributed transactional key-value database that also provides classical key-vlue APIs, but also transactional APIs with ACID compliance.

[Sonic](https://crates.io/crates/sonic-server) is a fast, lightweight and schema-less search backend similar to Elasticsearch in some use-cases.

[Hyper](https://github.com/hyperium/hyper) is a fast and correct HTTP library for Rust.

[Rocket](https://github.com/SergioBenitez/Rocket) is an async web framework for Rust with a focus on usability, security, extensibility, and speed.

[Clippy](https://rust-lang.github.io/rust-clippy/) is a collection of lints to catch common mistakes and improve your Rust code.

[Servo](https://github.com/servo/servo) is a prototype web browser engine written in the Rust language.

[Vector](https://vector.dev/) is a high-performance, end-to-end (agent & aggregator) observability data platform that puts the user in control of their observability data.

[RustPython](https://github.com/RustPython/RustPython) is a Python Interpreter written in Rust.

[Miri](https://github.com/rust-lang/miri) is an interpreter for Rust's mid-level intermediate representation. It can run binaries and test suites of cargo projects and detect certain classes of undefined behavior. Miri will alsowill also tell you about memory leaks: when there is memory still allocated at the end of the execution, and that memory is not reachable from a global static, Miri will raise an error.

[Chalk](https://rust-lang.github.io/chalk/book/) is an implementation and definition of the Rust trait system using a PROLOG-like logic solver.

[stdarch](https://doc.rust-lang.org/stable/core/arch/) is Rust's standard library vendor-specific APIs and run-time feature detection.

[Simpleinfra](https://github.com/rust-lang/simpleinfra) is rep that contains the tools and automation written by the Rust infrastructure team to manage our services. Using some of the tools in this repo require privileges only infra team members have.

[Rustlings](https://github.com/rust-lang/rustlings) is a small set of exercises to get you used to reading and writing Rust code.

[Krustlet](https://krustlet.dev/) acts as a Kubernetes Kubelet(written in Rust) by listening on the event stream for new pods that the scheduler assigns to it based on specific Kubernetes [tolerations](https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/). The project is currently experimental.

## Rust-based Operating Systems

[Redox](https://www.redox-os.org) is a Unix-like Operating System written in Rust, aiming to bring the innovations of Rust to a modern microkernel and full set of applications. Acitvely being developed by [Jeremy Soeller](https://gitlab.redox-os.org/jackpot51).

[Bottlerocket OS](https://github.com/bottlerocket-os/bottlerocket) is an open-source Linux-based operating system meant for hosting containers. Bottlerocket focuses on security and maintainability, providing a reliable, consistent, and safe platform for container-based workloads.

[Tock](https://www.tockos.org) is an embedded operating system designed for running multiple concurrent, mutually distrustful applications on Cortex-M and RISC-V based embedded platforms. Tock's design centers around protection, both from potentially malicious applications and from device drivers. Tock uses two mechanisms to protect different components of the operating system. First, the kernel and device drivers are written in Rust, a systems programming language that provides compile-time memory safety, type safety and strict aliasing. Tock uses Rust to protect the kernel (the scheduler and hardware abstraction layer) from platform specific device drivers as well as isolate device drivers from each other. Second, Tock uses memory protection units to isolate applications from each other and the kernel.

[Rust on Chrome OS](https://chromium.googlesource.com/chromiumos/docs/+/master/rust_on_cros.md) is a document that provides information on creating Rust projects for installation within Chrome OS and Chrome OS SDK.

[Writing an OS in Rust ](https://os.phil-opp.com) is a blog series creates a small operating system in the Rust programming language by [Philipp Oppermann](https://github.com/phil-opp).

# Networking
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/82833053-d1687b80-9e71-11ea-8c6d-074100f2f54b.png">
  <br />
</p>

## Network Learning Resources

[AWS Certified Security - Specialty Certification](https://aws.amazon.com/certification/certified-security-specialty/)

[Microsoft Certified: Azure Security Engineer Associate](https://docs.microsoft.com/en-us/learn/certifications/azure-security-engineer)

[Google Cloud Certified Professional Cloud Security Engineer](https://cloud.google.com/certification/cloud-security-engineer)

[Cisco Security Certifications](https://www.cisco.com/c/en/us/training-events/training-certifications/certifications/security.html)

[The Red Hat Certified Specialist in Security: Linux](https://www.redhat.com/en/services/training/ex415-red-hat-certified-specialist-security-linux-exam)

[Linux Professional Institute LPIC-3 Enterprise Security Certification](https://www.lpi.org/our-certifications/lpic-3-303-overview)

[Cybersecurity Training and Courses from IBM Skills](https://www.ibm.com/skills/topics/cybersecurity/)

[Cybersecurity Courses and Certifications by Offensive Security](https://www.offensive-security.com/courses-and-certifications/)

[Citrix Certified Associate – Networking(CCA-N)](http://training.citrix.com/cms/index.php/certification/networking/)

[Citrix Certified Professional – Virtualization(CCP-V)](https://www.globalknowledge.com/us-en/training/certification-prep/brands/citrix/section/virtualization/citrix-certified-professional-virtualization-ccp-v/)

[CCNP Routing and Switching](https://learningnetwork.cisco.com/s/ccnp-enterprise)

[Certified Information Security Manager(CISM)](https://www.isaca.org/credentialing/cism)

[Wireshark Certified Network Analyst (WCNA)](https://www.wiresharktraining.com/certification.html)

[Juniper Networks Certification Program Enterprise (JNCP)](https://www.juniper.net/us/en/training/certification/)

[Networking courses and specializations from Coursera](https://www.coursera.org/browse/information-technology/networking)

[Network & Security Courses from Udemy](https://www.udemy.com/courses/it-and-software/network-and-security/)

[Network & Security Courses from edX](https://www.edx.org/learn/cybersecurity)

## Networking Tools & Concepts

[Qt Network Authorization](https://doc.qt.io/qt-6/qtnetworkauth-index.html) is a tool that provides a set of APIs that enable Qt applications to obtain limited access to online accounts and HTTP services without exposing users' passwords.

[cURL](https://curl.se/) is a computer software project providing a library and command-line tool for transferring data using various network protocols(HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, DICT, TELNET, LDAP LDAPS, MQTT, POP3, POP3S, RTMP, RTMPS, RTSP, SCP, SFTP, SMB, SMBS, SMTP or SMTPS). cURL is also used in cars, television sets, routers, printers, audio equipment, mobile phones, tablets, settop boxes, media players and is the Internet transfer engine for thousands of software applications in over ten billion installations.

[cURL Fuzzer](https://github.com/curl/curl-fuzzer) is a quality assurance testing for the curl project.

[DoH](https://github.com/curl/doh) is a stand-alone application for DoH (DNS-over-HTTPS) name resolves and lookups.

[Authelia](https://www.authelia.com/) is an open-source highly-available authentication server providing single sign-on capability and two-factor authentication to applications running behind [NGINX](https://nginx.org/en/).

[nginx(engine x)](https://nginx.org/en/) is an HTTP and reverse proxy server, a mail proxy server, and a generic TCP/UDP proxy server, originally written by Igor Sysoev.

[Proxmox Virtual Environment(VE)](https://www.proxmox.com/en/) is a complete open-source platform for enterprise virtualization. It inlcudes a built-in web interface that you can easily manage VMs and containers, software-defined storage and networking, high-availability clustering, and multiple out-of-the-box tools on a single solution.

[Wireshark](https://www.wireshark.org/) is a very popular network protocol analyzer that is commonly used for network troubleshooting, analysis, and communications protocol development. Learn more about the other useful [Wireshark Tools](https://wiki.wireshark.org/Tools) available.

[HTTPie](https://github.com/httpie/httpie) is a command-line HTTP client. Its goal is to make CLI interaction with web services as human-friendly as possible. HTTPie is designed for testing, debugging, and generally interacting with APIs & HTTP servers.

[HTTPStat](https://github.com/reorx/httpstat) is a tool that visualizes curl statistics in a simple layout.

[Wuzz](https://github.com/asciimoo/wuzz) is an interactive cli tool for HTTP inspection. It can be used to inspect/modify requests copied from the browser's network inspector with the "copy as cURL" feature.

[Websocat](https://github.com/vi/websocat) is a ommand-line client for WebSockets, like netcat (or curl) for ws:// with advanced socat-like functions.

   - Connection: In networking, a connection refers to pieces of related information that are transferred through a network. This generally infers that a connection is built before the data transfer (by following the procedures laid out in a protocol) and then is deconstructed at the at the end of the data transfer.

   - Packet: A packet is, generally speaking, the most basic unit that is transferred over a network. When communicating over a network, packets are the envelopes that carry your data (in pieces) from one end point to the other.

Packets have a header portion that contains information about the packet including the source and destination, timestamps, network hops. The main portion of a packet contains the actual data being transferred. It is sometimes called the body or the payload.

   - Network Interface: A network interface can refer to any kind of software interface to networking hardware. For instance, if you have two network cards in your computer, you can control and configure each network interface associated with them individually.

A network interface may be associated with a physical device, or it may be a representation of a virtual interface. The "loop-back" device, which is a virtual interface to the local machine, is an example of this.

   - LAN: LAN stands for "local area network". It refers to a network or a portion of a network that is not publicly accessible to the greater internet. A home or office network is an example of a LAN.

   - WAN: WAN stands for "wide area network". It means a network that is much more extensive than a LAN. While WAN is the relevant term to use to describe large, dispersed networks in general, it is usually meant to mean the internet, as a whole.
If an interface is connected to the WAN, it is generally assumed that it is reachable through the internet.

   - Protocol: A protocol is a set of rules and standards that basically define a language that devices can use to communicate. There are a great number of protocols in use extensively in networking, and they are often implemented in different layers.

Some low level protocols are TCP, UDP, IP, and ICMP. Some familiar examples of application layer protocols, built on these lower protocols, are HTTP (for accessing web content), SSH, TLS/SSL, and FTP.

   - Port: A port is an address on a single machine that can be tied to a specific piece of software. It is not a physical interface or location, but it allows your server to be able to communicate using more than one application.

   - Firewall: A firewall is a program that decides whether traffic coming into a server or going out should be allowed. A firewall usually works by creating rules for which type of traffic is acceptable on which ports. Generally, firewalls block ports that are not used by a specific application on a server.

   - NAT: Network address translation is a way to translate requests that are incoming into a routing server to the relevant devices or servers that it knows about in the LAN. This is usually implemented in physical LANs as a way to route requests through one IP address to the necessary backend servers.

   - VPN: Virtual private network is a means of connecting separate LANs through the internet, while maintaining privacy. This is used as a means of connecting remote systems as if they were on a local network, often for security reasons.

## Network Layers

While networking is often discussed in terms of topology in a horizontal way, between hosts, its implementation is layered in a vertical fashion throughout a computer or network. This means is that there are multiple technologies and protocols that are built on top of each other in order for communication to function more easily. Each successive, higher layer abstracts the raw data a little bit more, and makes it simpler to use for applications and users. It also allows you to leverage lower layers in new ways without having to invest the time and energy to develop the protocols and applications that handle those types of traffic.

As data is sent out of one machine, it begins at the top of the stack and filters downwards. At the lowest level, actual transmission to another machine takes place. At this point, the data travels back up through the layers of the other computer. Each layer has the ability to add its own "wrapper" around the data that it receives from the adjacent layer, which will help the layers that come after decide what to do with the data when it is passed off.

One method of talking about the different layers of network communication is the OSI model. OSI stands for [Open Systems Interconnect](https://en.wikipedia.org/wiki/OSI_model).This model defines seven separate layers. The layers in this model are:

   - Application: The application layer is the layer that the users and user-applications most often interact with. Network communication is discussed in terms of availability of resources, partners to communicate with, and data synchronization.

   - Presentation: The presentation layer is responsible for mapping resources and creating context. It is used to translate lower level networking data into data that applications expect to see.

   - Session: The session layer is a connection handler. It creates, maintains, and destroys connections between nodes in a persistent way.

   - Transport: The transport layer is responsible for handing the layers above it a reliable connection. In this context, reliable refers to the ability to verify that a piece of data was received intact at the other end of the connection. This layer can resend information that has been dropped or corrupted and can acknowledge the receipt of data to remote computers.

   - Network: The network layer is used to route data between different nodes on the network. It uses addresses to be able to tell which computer to send information to. This layer can also break apart larger messages into smaller chunks to be reassembled on the opposite end.

   - Data Link: This layer is implemented as a method of establishing and maintaining reliable links between different nodes or devices on a network using existing physical connections.

   - Physical: The physical layer is responsible for handling the actual physical devices that are used to make a connection. This layer involves the bare software that manages physical connections as well as the hardware itself (like Ethernet).

The TCP/IP model, more commonly known as the Internet protocol suite, is another layering model that is simpler and has been widely adopted.It defines the four separate layers, some of which overlap with the OSI model:

   - Application: In this model, the application layer is responsible for creating and transmitting user data between applications. The applications can be on remote systems, and should appear to operate as if locally to the end user.
The communication takes place between peers network.

   - Transport: The transport layer is responsible for communication between processes. This level of networking utilizes ports to address different services. It can build up unreliable or reliable connections depending on the type of protocol used.

   - Internet: The internet layer is used to transport data from node to node in a network. This layer is aware of the endpoints of the connections, but does not worry about the actual connection needed to get from one place to another. IP addresses are defined in this layer as a way of reaching remote systems in an addressable manner.

   - Link: The link layer implements the actual topology of the local network that allows the internet layer to present an addressable interface. It establishes connections between neighboring nodes to send data.

### Interfaces
**Interfaces** are networking communication points for your computer. Each interface is associated with a physical or virtual networking device. Typically, your server will have one configurable network interface for each Ethernet or wireless internet card you have. In addition, it will define a virtual network interface called the "loopback" or localhost interface. This is used as an interface to connect applications and processes on a single computer to other applications and processes. You can see this referenced as the "lo" interface in many tools.

## Network Protocols

Networking works by piggybacks on a number of different protocols on top of each other. In this way, one piece of data can be transmitted using multiple protocols encapsulated within one another.

**Media Access Control(MAC)** is a communications protocol that is used to distinguish specific devices. Each device is supposed to get a unique MAC address during the manufacturing process that differentiates it from every other device on the internet. Addressing hardware by the MAC address allows you to reference a device by a unique value even when the software on top may change the name for that specific device during operation. Media access control is one of the only protocols from the link layer that you are likely to interact with on a regular basis.

**The IP protocol** is one of the fundamental protocols that allow the internet to work. IP addresses are unique on each network and they allow machines to address each other across a network. It is implemented on the internet layer in the IP/TCP model. Networks can be linked together, but traffic must be routed when crossing network boundaries. This protocol assumes an unreliable network and multiple paths to the same destination that it can dynamically change between. There are a number of different implementations of the protocol. The most common implementation today is IPv4, although IPv6 is growing in popularity as an alternative due to the scarcity of IPv4 addresses available and improvements in the protocols capabilities.

**ICMP: internet control message protocol** is used to send messages between devices to indicate the availability or error conditions. These packets are used in a variety of network diagnostic tools, such as ping and traceroute. Usually ICMP packets are transmitted when a packet of a different kind meets some kind of a problem. Basically, they are used as a feedback mechanism for network communications.

**TCP: Transmission control protocol** is implemented in the transport layer of the IP/TCP model and is used to establish reliable connections. TCP is one of the protocols that encapsulates data into packets. It then transfers these to the remote end of the connection using the methods available on the lower layers. On the other end, it can check for errors, request certain pieces to be resent, and reassemble the information into one logical piece to send to the application layer. The protocol builds up a connection prior to data transfer using a system called a three-way handshake. This is a way for the two ends of the communication to acknowledge the request and agree upon a method of ensuring data reliability. After the data has been sent, the connection is torn down using a similar four-way handshake. TCP is the protocol of choice for many of the most popular uses for the internet, including WWW, FTP, SSH, and email. It is safe to say that the internet we know today would not be here without TCP.

**UDP: User datagram protocol** is a popular companion protocol to TCP and is also implemented in the transport layer. The fundamental difference between UDP and TCP is that UDP offers unreliable data transfer. It does not verify that data has been received on the other end of the connection. This might sound like a bad thing, and for many purposes, it is. However, it is also extremely important for some functions. It’s not required to wait for confirmation that the data was received and forced to resend data, UDP is much faster than TCP. It does not establish a connection with the remote host, it simply fires off the data to that host and doesn't care if it is accepted or not. Since UDP is a simple transaction, it is useful for simple communications like querying for network resources. It also doesn't maintain a state, which makes it great for transmitting data from one machine to many real-time clients. This makes it ideal for VOIP, games, and other applications that cannot afford delays.

**HTTP: Hypertext transfer protocol** is a protocol defined in the application layer that forms the basis for communication on the web. HTTP defines a number of functions that tell the remote system what you are requesting. For instance, GET, POST, and DELETE all interact with the requested data in a different way.

**FTP: File transfer protocol** is in the application layer and provides a way of transferring complete files from one host to another. It is inherently insecure, so it is not recommended for any externally facing network unless it is implemented as a public, download-only resource.

**DNS: Domain name system** is an application layer protocol used to provide a human-friendly naming mechanism for internet resources. It is what ties a domain name to an IP address and allows you to access sites by name in your browser.

**SSH: Secure shell** is an encrypted protocol implemented in the application layer that can be used to communicate with a remote server in a secure way. Many additional technologies are built around this protocol because of its end-to-end encryption and ubiquity. There are many other protocols that we haven't covered that are equally important. However, this should give you a good overview of some of the fundamental technologies that make the internet and networking possible.

[REST(REpresentational State Transfer)](https://www.codecademy.com/articles/what-is-rest) is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other.

[JSON Web Token (JWT)](https://jwt.io) is a compact URL-safe means of representing claims to be transferred between two parties. The claims in a JWT are encoded as a JSON object that is digitally signed using JSON Web Signature (JWS).

[OAuth 2.0](https://oauth.net/2/) is an open source authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Amazon, Google, Facebook, Microsoft, Twitter GitHub, and DigitalOcean. It works by delegating user authentication to the service that hosts the user account, and authorizing third-party applications to access the user account.

# Kubernetes
[Back to the Top](https://github.com/mikeroyal/ebpf-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/95383873-a884d800-08a0-11eb-8eaf-57af5b119f56.png">
  <br />
</p>

## Kubernetes Learning Resources

[Kubernetes (K8s)](https://kubernetes.io/) is an open-source system for automating deployment, scaling, and management of containerized applications.

[Getting Kubernetes Certifications](https://training.linuxfoundation.org/certification/catalog/?_sft_technology=kubernetes)

[Getting started with Kubernetes on AWS](https://aws.amazon.com/kubernetes/)

[Kubernetes on Microsoft Azure](https://azure.microsoft.com/en-us/topic/what-is-kubernetes/)

[Intro to Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard)

[Azure Red Hat OpenShift ](https://azure.microsoft.com/en-us/services/openshift/)

[Getting started with Google Cloud](https://cloud.google.com/learn/what-is-kubernetes)

[Getting started with Kubernetes on Red Hat](https://www.redhat.com/en/topics/containers/what-is-kubernetes)

[Getting started with Kubernetes on IBM](https://www.ibm.com/cloud/learn/kubernetes)

[Red Hat OpenShift on IBM Cloud](https://www.ibm.com/cloud/openshift)

[Enable OpenShift Virtualization on Red Hat OpenShift](https://developers.redhat.com/blog/2020/08/28/enable-openshift-virtualization-on-red-hat-openshift/)

[YAML basics in Kubernetes](https://developer.ibm.com/technologies/containers/tutorials/yaml-basics-and-usage-in-kubernetes/)

[Elastic Cloud on Kubernetes](https://www.elastic.co/elastic-cloud-kubernetes)

[Docker and Kubernetes](https://www.docker.com/products/kubernetes)

[Running Apache Spark on Kubernetes](http://spark.apache.org/docs/latest/running-on-kubernetes.html)

[Kubernetes Across VMware vRealize Automation](https://blogs.vmware.com/management/2019/06/kubernetes-across-vmware-cloud-automation-services.html)

[VMware Tanzu Kubernetes Grid](https://tanzu.vmware.com/kubernetes-grid)

[All the Ways VMware Tanzu Works with AWS](https://tanzu.vmware.com/content/blog/all-the-ways-vmware-tanzutm-works-with-aws)

[VMware Tanzu Education](https://tanzu.vmware.com/education)

[Using Ansible in a Cloud-Native Kubernetes Environment](https://www.ansible.com/blog/how-useful-is-ansible-in-a-cloud-native-kubernetes-environment)

[Managing Kubernetes (K8s) objects with Ansible](https://docs.ansible.com/ansible/latest/collections/community/kubernetes/k8s_module.html)

[Setting up a Kubernetes cluster using Vagrant and Ansible](https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/)

[Running MongoDB with Kubernetes](https://www.mongodb.com/kubernetes)

[Kubernetes Fluentd](https://docs.fluentd.org/v/0.12/articles/kubernetes-fluentd)

[Understanding the new GitLab Kubernetes Agent](https://about.gitlab.com/blog/2020/09/22/introducing-the-gitlab-kubernetes-agent/)

[Intro Local Process with Kubernetes for Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/introducing-local-process-with-kubernetes-for-visual-studio%E2%80%AF2019/)

[Kubernetes Contributors](https://www.kubernetes.dev/)

[KubeAcademy from VMware](https://kube.academy/)

[Kubernetes Tutorials from Pulumi](https://www.pulumi.com/docs/tutorials/kubernetes/)

[Kubernetes Playground by Katacoda](https://www.katacoda.com/courses/kubernetes/playground)

[Scalable Microservices with Kubernetes course from Udacity ](https://www.udacity.com/course/scalable-microservices-with-kubernetes--ud615)

## Kubernetes Tools, Frameworks, and Projects 

[Open Container Initiative](https://opencontainers.org/about/overview/) is an open governance structure for the express purpose of creating open industry standards around container formats and runtimes.

[Buildah](https://buildah.io/) is a command line tool to build Open Container Initiative (OCI) images. It can be used with Docker, Podman, Kubernetes.

[Podman](https://podman.io/) is a daemonless, open source, Linux native tool designed to make it easy to find, run, build, share and deploy applications using Open Containers Initiative (OCI) Containers and Container Images. Podman provides a command line interface (CLI) familiar to anyone who has used the Docker Container Engine.

[Containerd](https://containerd.io) is a daemon that manages the complete container lifecycle of its host system, from image transfer and storage to container execution and supervision to low-level storage to network attachments and beyond. It is available for Linux and Windows. 

[Google Kubernetes Engine (GKE)](https://cloud.google.com/kubernetes-engine/) is a managed, production-ready environment for running containerized applications.

[Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/services/kubernetes-service/) is serverless Kubernetes, with a integrated continuous integration and continuous delivery (CI/CD) experience, and enterprise-grade security and governance. Unite your development and operations teams on a single platform to rapidly build, deliver, and scale applications with confidence.

[Amazon EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) is a tool that runs Kubernetes control plane instances across multiple Availability Zones to ensure high availability.

[AWS Controllers for Kubernetes (ACK)](https://aws.amazon.com/blogs/containers/aws-controllers-for-kubernetes-ack/) is a new tool that lets you directly manage AWS services from Kubernetes. ACK makes it simple to build scalable and highly-available Kubernetes applications that utilize AWS services.

[Container Engine for Kubernetes (OKE)](https://www.oracle.com/cloud-native/container-engine-kubernetes/) is an Oracle-managed container orchestration service that can reduce the time and cost to build modern cloud native applications. Unlike most other vendors, Oracle Cloud Infrastructure provides Container Engine for Kubernetes as a free service that runs on higher-performance, lower-cost compute.

[Anthos](https://cloud.google.com/anthos/docs/concepts/overview) is a modern application management platform that provides a consistent development and operations experience for cloud and on-premises environments.

[Red Hat Openshift](https://www.openshift.com/) is a fully managed Kubernetes platform that provides a foundation for on-premises, hybrid, and multicloud deployments. 

[OKD](https://okd.io/) is a community distribution of Kubernetes optimized for continuous application development and multi-tenant deployment. OKD adds developer and operations-centric tools on top of Kubernetes to enable rapid application development, easy deployment and scaling, and long-term lifecycle maintenance for small and large teams.

[Odo](https://odo.dev/) is a fast, iterative, and straightforward CLI tool for developers who write, build, and deploy applications on Kubernetes and OpenShift.

[Kata Operator](https://github.com/openshift/kata-operator) is an operator to perform lifecycle management (install/upgrade/uninstall) of [Kata Runtime](https://katacontainers.io/) on Openshift as well as Kubernetes cluster.

[Thanos](https://thanos.io/) is a set of components that can be composed into a highly available metric system with unlimited storage capacity, which can be added seamlessly on top of existing Prometheus deployments.

[OpenShift Hive](https://github.com/openshift/hive) is an operator which runs as a service on top of Kubernetes/OpenShift. The Hive service can be used to provision and perform initial configuration of OpenShift 4 clusters.

[Rook](https://rook.io/) is a tool that turns distributed storage systems into self-managing, self-scaling, self-healing storage services. It automates the tasks of a storage administrator: deployment, bootstrapping, configuration, provisioning, scaling, upgrading, migration, disaster recovery, monitoring, and resource management.

[VMware Tanzu](https://tanzu.vmware.com/tanzu) is a centralized management platform for consistently operating and securing your Kubernetes infrastructure and modern applications across multiple teams and private/public clouds.

[Kubespray](https://kubespray.io/) is a tool that combines Kubernetes and Ansible to easily install Kubernetes clusters that can be deployed on [AWS](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/aws.md), GCE, [Azure](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/azure.md), [OpenStack](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/openstack.md), [vSphere](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/vsphere.md), [Packet](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/packet.md) (bare metal), Oracle Cloud Infrastructure (Experimental), or Baremetal.

[KubeInit](https://github.com/kubeinit/kubeinit) provides Ansible playbooks and roles for the deployment and configuration of multiple Kubernetes distributions.

[Rancher](https://rancher.com/) is a complete software stack for teams adopting containers. It addresses the operational and security challenges of managing multiple Kubernetes clusters, while providing DevOps teams with integrated tools for running containerized workloads.

[K3s](https://github.com/rancher/k3s) is a highly available, certified Kubernetes distribution designed for production workloads in unattended, resource-constrained, remote locations or inside IoT appliances. 

[Helm](https://helm.sh/) is a Kubernetes Package Manager tool that makes it easier to install and manage Kubernetes applications.

[Knative](https://knative.dev/) is a Kubernetes-based platform to build, deploy, and manage modern serverless workloads. Knative takes care of the operational overhead details of networking, autoscaling (even to zero), and revision tracking. 

[KubeFlow](https://www.kubeflow.org/) is a tool dedicated to making deployments of machine learning (ML) workflows on Kubernetes simple, portable and scalable.

[Kubebox](https://github.com/astefanutti/kubebox) is a Terminal and Web console for Kubernetes.

[Kubsec](https://github.com/controlplaneio/kubesec) is a Security risk analysis for Kubernetes resources.

[Replex](https://www.replex.io/) is a Kubernetes Governance and Cost Management for the Cloud-Native Enterprise.

[Virtual Kubelet](https://virtual-kubelet.io/) is an open-source [Kubernetes kubelet](https://kubernetes.io/docs/reference/generated/kubelet/) implementation that masquerades as a kubelet.

[Telepresence](https://www.telepresence.io/) is a fast, local development for Kubernetes and OpenShift microservices.

[Weave Scope](https://www.weave.works/oss/scope/) is a tool that automatically detects processes, containers, hosts. No kernel modules, no agents, no special libraries, no coding. It seamless integration with Docker, Kubernetes, DCOS and AWS ECS.

[Nuclio](https://nuclio.io/) is a high-performance "serverless" framework focused on data, I/O, and compute intensive workloads. It is well integrated with popular data science tools, such as [Jupyter](https://jupyter.org/) and [Kubeflow](https://www.kubeflow.org/); supports a variety of data and streaming sources; and supports execution over CPUs and GPUs. 

[Supergiant Control](https://github.com/supergiant/control) is a tool that manages the lifecycle of clusters on your infrastructure and allows deployment of applications via HELM. Its deployment and configuration workflows will help you to get up and running with Kubernetes faster.

[Supergiant Capacity - Beta](https://github.com/supergiant/capacity) is a tool that ensures that the right hardware is available for the required resource load of your Kubernetes cluster at any given time. This helps prevent over-provisioning of your container environment and overspending on your hardware budget. 

[Test suite for Kubernetes](https://github.com/mrahbar/k8s-testsuite) is a test suite consists of two Helm charts for network bandwith testing and load testing a Kuberntes cluster. 

[Keel](https://github.com/keel-hq/keel) is a Kubernetes Operator to automate Helm, DaemonSet, StatefulSet & Deployment updates.

[Kube Monkey](https://github.com/asobti/kube-monkey) is an implementation of Netflix's Chaos Monkey for Kubernetes clusters. It randomly deletes Kubernetes (k8s) pods in the cluster encouraging and validating the development of failure-resilient services.

[Kube State Metrics (KSM)](https://github.com/kubernetes/kube-state-metrics) is a simple service that listens to the Kubernetes API server and generates metrics about the state of the objects. It's not focused on the health of the individual Kubernetes components, but rather on the health of the various objects inside, such as deployments, nodes and pods.

[Sonobuoy](https://sonobuoy.io/) is a diagnostic tool that makes it easier to understand the state of a Kubernetes cluster by running a choice of configuration tests in an accessible and non-destructive manner.

[PowerfulSeal](https://github.com/powerfulseal/powerfulseal) is a powerful testing tool for your Kubernetes clusters, so that you can detect problems as early as possible.

[Test Infra](https://github.com/kubernetes/test-infra) is a repository contains tools and configuration files for the testing and automation needs of the Kubernetes project.

[cAdvisor (Container Advisor)](https://github.com/google/cadvisor) is a tool that provides container users an understanding of the resource usage and performance characteristics of their running containers. It's a running daemon that collects, aggregates, processes, and exports information about running containers. Specifically, for each container it keeps resource isolation parameters, historical resource usage, histograms of complete historical resource usage and network statistics. 

[Etcd](https://etcd.io/) is a distributed key-value store that provides a reliable way to store data that needs to be accessed by a distributed system or cluster of machines. Etcd is used as the backend for service discovery and stores cluster state and configuration for Kubernetes.

[OpenEBS](https://openebs.io/) is a Kubernetes-based tool to create stateful applications using Container Attached Storage.

[Container Storage Interface (CSI)](https://www.architecting.it/blog/container-storage-interface/) is an API that lets container orchestration platforms like Kubernetes seamlessly communicate with stored data via a plug-in.

[MicroK8s](https://microk8s.io/) is a tool that delivers the full Kubernetes experience. In a Fully containerized deployment with compressed over-the-air updates for ultra-reliable operations. It is supported on Linux, Windows, and MacOS.

[Charmed Kubernetes](https://ubuntu.com/kubernetes/features) is a well integrated, turn-key, conformant Kubernetes platform, optimized for your multi-cloud environments developed by Canonical.

[Grafana Kubernetes App](https://grafana.com/grafana/plugins/grafana-kubernetes-app) is a toll that allows you to monitor your Kubernetes cluster's performance. It includes 4 dashboards, Cluster, Node, Pod/Container and Deployment. It allows for the automatic deployment of the required Prometheus exporters and a default scrape config to use with your in cluster Prometheus deployment.

[KubeEdge](https://kubeedge.io/en/) is an open source system for extending native containerized application orchestration capabilities to hosts at Edge.It is built upon kubernetes and provides fundamental infrastructure support for network, app. deployment and metadata synchronization between cloud and edge.

[Lens](https://k8slens.dev/)  is the most powerful IDE for people who need to deal with Kubernetes clusters on a daily basis. It has support for MacOS, Windows and Linux operating systems.

[kind](https://kind.sigs.k8s.io/) is a tool for running local Kubernetes clusters using Docker container “nodes”. It was primarily designed for testing Kubernetes itself, but may be used for local development or CI.

[Flux CD](https://fluxcd.io/) is a tool that automatically ensures that the state of your Kubernetes cluster matches the configuration you've supplied in Git. It uses an operator in the cluster to trigger deployments inside Kubernetes, which means that you don't need a separate continuous delivery tool.


# Databases
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

<p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/119279004-daec0700-bbdd-11eb-9662-b1fc86ec8448.png">
  <br />
</p>

 <p align="center">
 <img src="https://user-images.githubusercontent.com/45159366/119279002-da537080-bbdd-11eb-9d7a-44efb52f3506.png">
  <br />
</p>

## SQL/NoSQL Learning Resources

[SQL](https://en.wikipedia.org/wiki/SQL) is a standard language for storing, manipulating and retrieving data in relational databases.

[NoSQL](https://www.ibm.com/cloud/blog/sql-vs-nosql) is a database that is interchangeably referred to as "nonrelational, or "non-SQL" to highlight that the database can handle huge volumes of rapidly changing, unstructured data in different ways than a relational (SQL-based) database with rows and tables.

[Transact-SQL(T-SQL)](https://docs.microsoft.com/en-us/sql/t-sql/language-reference) is a Microsoft extension of SQL with all of the tools and applications communicating to a SQL database by sending T-SQL commands.

[Introduction to Transact-SQL](https://docs.microsoft.com/en-us/learn/modules/introduction-to-transact-sql/)

[SQL Tutorial by W3Schools](https://www.w3schools.com/sql/)

[Learn SQL Skills Online from Coursera](https://www.coursera.org/courses?query=sql)

[SQL Courses Online from Udemy](https://www.udemy.com/topic/sql/)

[SQL Online Training Courses from LinkedIn Learning](https://www.linkedin.com/learning/topics/sql)

[Learn SQL For Free from Codecademy](https://www.codecademy.com/learn/learn-sql)

[GitLab's SQL Style Guide](https://about.gitlab.com/handbook/business-ops/data-team/platform/sql-style-guide/)

[OracleDB SQL Style Guide Basics](https://oracle.readthedocs.io/en/latest/sql/basics/style-guide.html)

[Tableau CRM: BI Software and Tools](https://www.salesforce.com/products/crm-analytics/overview/)

[Databases on AWS](https://aws.amazon.com/products/databases/)

[Best Practices and Recommendations for SQL Server Clustering in AWS EC2.](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/aws-sql-clustering.html)

[Connecting from Google Kubernetes Engine to a Cloud SQL instance.](https://cloud.google.com/sql/docs/mysql/connect-kubernetes-engine)

[Educational Microsoft Azure SQL resources](https://docs.microsoft.com/en-us/sql/sql-server/educational-sql-resources?view=sql-server-ver15)

[MySQL Certifications](https://www.mysql.com/certification/)

[SQL vs. NoSQL Databases: What's the Difference?](https://www.ibm.com/cloud/blog/sql-vs-nosql)

[What is NoSQL?](https://aws.amazon.com/nosql/)

## SQL/NoSQL Tools and Databases

[Netdata](https://github.com/netdata/netdata) is high-fidelity infrastructure monitoring and troubleshooting, real-time monitoring Agent collects thousands of metrics from systems, hardware, containers, and applications with zero configuration. It runs permanently on all your physical/virtual servers, containers, cloud deployments, and edge/IoT devices, and is perfectly safe to install on your systems mid-incident without any preparation.

[Azure Data Studio](https://github.com/Microsoft/azuredatastudio) is an open source data management tool that enables working with SQL Server, Azure SQL DB and SQL DW from Windows, macOS and Linux.

[Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)  is the intelligent, scalable, relational database service built for the cloud. It’s evergreen and always up to date, with AI-powered and automated features that optimize performance and durability for you. Serverless compute and Hyperscale storage options automatically scale resources on demand, so you can focus on building new applications without worrying about storage size or resource management.

[Azure SQL Managed Instance](https://azure.microsoft.com/en-us/services/azure-sql/sql-managed-instance/) is a fully managed SQL Server Database engine instance that's hosted in Azure and placed in your network. This deployment model makes it easy to lift and shift your on-premises applications to the cloud with very few application and database changes. Managed instance has split compute and storage components.

[Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) is a limitless analytics service that brings together enterprise data warehousing and Big Data analytics. It gives you the freedom to query data on your terms, using either serverless or provisioned resources at scale. It brings together the best of the SQL technologies used in enterprise data warehousing, Spark technologies used in big data analytics, and Pipelines for data integration and ETL/ELT.

[MSSQL for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) is an extension for developing Microsoft SQL Server, Azure SQL Database and SQL Data Warehouse everywhere with a rich set of functionalities.

[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/en-us/sql/ssdt/download-sql-server-data-tools-ssdt) is a development tool for building SQL Server relational databases, Azure SQL Databases, Analysis Services (AS) data models, Integration Services (IS) packages, and Reporting Services (RS) reports. With SSDT, a developer can design and deploy any SQL Server content type with the same ease as they would develop an application in Visual Studio or Visual Studio Code.

[Bulk Copy Program](https://docs.microsoft.com/en-us/sql/tools/bcp-utility) is a command-line tool that comes with Microsoft SQL Server. BCP, allows you to import and export large amounts of data in and out of SQL Server databases quickly snd efficeiently.

[SQL Server Migration Assistant](https://www.microsoft.com/en-us/download/details.aspx?id=54258) is a tool from Microsoft that simplifies database migration process from Oracle to SQL Server, Azure SQL Database, Azure SQL Database Managed Instance and Azure SQL Data Warehouse.

[SQL Server Integration Services](https://docs.microsoft.com/en-us/sql/integration-services/sql-server-integration-services?view=sql-server-ver15) is a development platform for building enterprise-level data integration and data transformations solutions. Use Integration Services to solve complex business problems by copying or downloading files, loading data warehouses, cleansing and mining data, and managing SQL Server objects and data.

[SQL Server Business Intelligence(BI)](https://www.microsoft.com/en-us/sql-server/sql-business-intelligence) is a collection of tools in Microsoft's SQL Server for transforming raw data into information businesses can use to make decisions.

[Tableau](https://www.tableau.com/) is a Data Visualization software used in relational databases, cloud databases, and spreadsheets. Tableau was acquired by [Salesforce in August 2019](https://investor.salesforce.com/press-releases/press-release-details/2019/Salesforce-Completes-Acquisition-of-Tableau/default.aspx).

[DataGrip](https://www.jetbrains.com/datagrip/) is a professional DataBase IDE developed by Jet Brains that provides context-sensitive code completion, helping you to write SQL code faster. Completion is aware of the tables structure, foreign keys, and even database objects created in code you're editing.

[RStudio](https://rstudio.com/) is an integrated development environment for R and Python, with a console, syntax-highlighting editor that supports direct code execution, and tools for plotting, history, debugging and workspace management.

[MySQL](https://www.mysql.com/) is a fully managed database service to deploy cloud-native applications using the world's most popular open source database.

[PostgreSQL](https://www.postgresql.org/) is a powerful, open source object-relational database system with over 30 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.

[Amazon DynamoDB](https://aws.amazon.com/dynamodb/) is a key-value and document database that delivers single-digit millisecond performance at any scale. It is a fully managed, multiregion, multimaster, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications.

[Apache Cassandra™](https://cassandra.apache.org/) is an open source NoSQL distributed database trusted by thousands of companies for scalability and high availability without compromising performance. Cassandra provides linear scalability and proven fault-tolerance on commodity hardware or cloud infrastructure make it the perfect platform for mission-critical data.

[Apache HBase™](https://hbase.apache.org/) is an open-source, NoSQL, distributed big data store. It enables random, strictly consistent, real-time access to petabytes of data. HBase is very effective for handling large, sparse datasets. HBase serves as a direct input and output to the Apache MapReduce framework for Hadoop, and works with Apache Phoenix to enable SQL-like queries over HBase tables.

[Hadoop Distributed File System (HDFS)](https://www.ibm.com/analytics/hadoop/hdfs) is a distributed file system that handles large data sets running on commodity hardware. It is used to scale a single Apache Hadoop cluster to hundreds (and even thousands) of nodes. HDFS is one of the major components of Apache Hadoop, the others being [MapReduce](https://www.ibm.com/analytics/hadoop/mapreduce) and [YARN](https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html).

[Apache Mesos](http://mesos.apache.org/) is a cluster manager that provides efficient resource isolation and sharing across distributed applications, or frameworks. It can run Hadoop, Jenkins, Spark, Aurora, and other frameworks on a dynamically shared pool of nodes.

[Apache Spark](https://spark.apache.org/) is a unified analytics engine for big data processing, with built-in modules for streaming, SQL, machine learning and graph processing.

[ElasticSearch](https://www.elastic.co/) is a search engine based on the Lucene library. It provides a distributed, multitenant-capable full-text search engine with an HTTP web interface and schema-free JSON documents. Elasticsearch is developed in Java.

[Logstash](https://www.elastic.co/products/logstash) is a tool for managing events and logs. When used generically, the term encompasses a larger system of log collection, processing, storage and searching activities.

[Kibana](https://www.elastic.co/products/kibana) is an open source data visualization plugin for Elasticsearch. It provides visualization capabilities on top of the content indexed on an Elasticsearch cluster. Users can create bar, line and scatter plots, or pie charts and maps on top of large volumes of data.

[Trino](https://trino.io/) is a Distributed SQL query engine for big data. It is able to tremendously speed up [ETL processes](https://docs.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl), allow them all to use standard SQL statement, and work with numerous data sources and targets all in the same system.

[Extract, transform, and load (ETL)](https://docs.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl) is a data pipeline used to collect data from various sources, transform the data according to business rules, and load it into a destination data store.

[Redis(REmote DIctionary Server)](https://redis.io/) is an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker. It provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams.

[FoundationDB](https://www.foundationdb.org/) is an open source distributed database designed to handle large volumes of structured data across clusters of commodity servers. It organizes data as an ordered key-value store and employs ACID transactions for all operations. It is especially well-suited for read/write workloads but also has excellent performance for write-intensive workloads. FoundationDB was acquired by [Apple in 2015](https://techcrunch.com/2015/03/24/apple-acquires-durable-database-company-foundationdb/).

[IBM DB2](https://www.ibm.com/analytics/db2) is a collection of hybrid data management products offering a complete suite of AI-empowered capabilities designed to help you manage both structured and unstructured data on premises as well as in private and public cloud environments. Db2 is built on an intelligent common SQL engine designed for scalability and flexibility.

[MongoDB](https://www.mongodb.com/) is a document database meaning it stores data in JSON-like documents.

[OracleDB](https://www.oracle.com/database/) is a powerful fully managed database helps developers manage business-critical data with the highest availability, reliability, and security.

[MariaDB](https://mariadb.com/) is an enterprise open source database solution for modern, mission-critical applications.

[SQLite](https://sqlite.org/index.html) is a C-language library that implements a small, fast, self-contained, high-reliability, full-featured, SQL database engine.SQLite is the most used database engine in the world. SQLite is built into all mobile phones and most computers and comes bundled inside countless other applications that people use every day.

[SQLite Database Browser](https://sqlitebrowser.org/) is an open source SQL tool that allows users to create, design and edits SQLite database files. It lets users show a log of all the SQL commands that have been issued by them and by the application itself.

[InfluxDB](https://www.influxdata.com/) is an open source time series platform.  This includes APIs for storing and querying data, processing it in the background for [ETL](https://docs.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl) or monitoring and alerting purposes, user dashboards, Internet of Things sensor data, and visualizing and exploring the data and more. It also has support for processing data from [Graphite](http://graphiteapp.org/).

[Atlas](https://github.com/Netflix/atlas) is an in-memory dimensional [time series database](https://en.wikipedia.org/wiki/Time_series_database).

[CouchbaseDB](https://www.couchbase.com/) is an open source distributed [multi-model NoSQL document-oriented database](https://en.wikipedia.org/wiki/Multi-model_database). It creates a key-value store with managed cache for sub-millisecond data operations, with purpose-built indexers for efficient queries and a powerful query engine for executing SQL queries.

[dbWatch](https://www.dbwatch.com/) is a complete database monitoring/management solution for SQL Server, Oracle, PostgreSQL, Sybase, MySQL and Azure. Designed for proactive management and automation of routine maintenance in large scale on-premise, hybrid/cloud database environments.

[Cosmos DB Profiler](https://hibernatingrhinos.com/products/cosmosdbprof) is a real-time visual debugger allowing a development team to gain valuable insight and perspective into their usage of Cosmos DB database. It identifies over a dozen suspicious behaviors from your application’s interaction with Cosmos DB.

[Adminer](https://www.adminer.org/) is an SQL management client tool for managing databases, tables, relations, indexes, users. Adminer has support for all the popular database management systems such as MySQL, MariaDB, PostgreSQL, SQLite, MS SQL, Oracle, Firebird, SimpleDB, Elasticsearch and MongoDB.

[DBeaver](https://dbeaver.io/) is an open source database tool for developers and database administrators. It offers supports for JDBC compliant databases such as MySQL, Oracle, IBM DB2, SQL Server, Firebird, SQLite, Sybase, Teradata, Firebird, Apache Hive, Phoenix, and Presto.

[DbVisualizer](https://dbvis.com/) is a SQL management tool that allows users to manage a wide range of databases such as Oracle, Sybase, SQL Server, MySQL, H3, and SQLite.

[AppDynamics Database](https://www.appdynamics.com/supported-technologies/database) is a management product for Microsoft SQL Server. With AppDynamics you can monitor and trend key performance metrics such as resource consumption, database objects, schema statistics and more, allowing you to proactively tune and fix issues in a High-Volume Production Environment.

[Toad](https://www.quest.com/toad/) is a SQL Server DBMS toolset developed by Quest. It increases productivity by using extensive automation, intuitive workflows, and built-in expertise. This SQL management tool resolve issues, manage change and promote the highest levels of code quality for both relational and non-relational databases.

[Lepide SQL Server](https://www.lepide.com/sql-storage-manager/) is an open source storage manager utility to analyse the performance of SQL Servers. It provides a complete overview of all configuration and permission changes being made to your SQL Server environment through an easy-to-use, graphical user interface.

[Sequel Pro](https://sequelpro.com/) is a fast MacOS database management tool for working with MySQL. This SQL management tool helpful for interacting with your database by easily to adding new databases, new tables, and new rows.

## Contribute

- [x] If would you like to contribute to this guide simply make a [Pull Request](https://github.com/mikeroyal/eBPF-Guide/pulls).


## License
[Back to the Top](https://github.com/mikeroyal/eBPF-Guide#table-of-contents)

Distributed under the [Creative Commons Attribution 4.0 International (CC BY 4.0) Public License](https://creativecommons.org/licenses/by/4.0/).

