# Awesome eBPF [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> A curated list of awesome projects related to eBPF.

> Note: eBPF is an exciting piece of technology, and it's ecosystem is constantly evolving. We'd love help from _you_ to keep this awesome list up to date, and improve its signal-to-noise ratio in anyway we can. Please feel free to leave [any feedback](https://github.com/zoidbergwill/awesome-ebpf/issues).

## Contents

-   [What is BPF?](#what-is-bpf)
-   [Resources](#resources)
-   [Projects based on, or related to eBPF](#projects-based-on-or-related-to-ebpf)
-   [Tutorials](#tutorials)
-   [Examples](#examples)
-   [The Code](#the-code)
-   [Tools and Utilities](#tools-and-utilities)
-   [Development and Community](#development-and-community)
-   [Other lists of resources on eBPF](#other-lists-of-resources-on-ebpf)
-   [Acknowledgement](#acknowledgement)
-   [Contributing To This List](#contribute)
-   [License](#license)

## What is BPF?

TODO: Update with concise overview of BPF (cBPF and eBPF), and what it's
used for already.

## Resources

### Generic Documentation and Presentations

If you are new to eBPF, you may want to try the links described as
“introduction” or ”documentation” in this section (although you might not want
to start with “kernel documentation”, which is dense).

-   [linux/Documentation/networking/filter.txt](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/networking/filter.txt).
    Kernel documentation: eBPF specification (somewhat outdated; information
    should still be valid, but not exhaustive).
-   [linux/Documentation/bpf/bpf_design_QA.txt](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/bpf/bpf_design_QA.txt).
    Kernel documentation: Frequently Asked Questions on eBPF design.
-   [IO Visor's Unofficial eBPF spec](https://github.com/iovisor/bpf-docs/blob/master/eBPF.md)
    Summary of eBPF syntax and operation codes.
-   Manual pages
    -   [`bpf(2)` man page](http://man7.org/linux/man-pages/man2/bpf.2.html)
        about the `bpf()` system call, used to manage BPF programs and maps
        from userspace.
    -   [`tc-bpf(8)` man page](http://man7.org/linux/man-pages/man8/tc-bpf.8.html)
        about using BPF with tc, including example commands and samples of
        code.
-   [Jesper Dangaard Brouer's documentation](https://prototype-kernel.readthedocs.io/en/latest/bpf/index.html):
    work in progress, contributions welcome.
-   [Cilum's BPF and XDP Reference Guide](http://docs.cilium.io/en/latest/bpf/)
    Generic documentation about most features of eBPF.
-   Emails from David Miller to the [xdp-newbies](http://vger.kernel.org/vger-lists.html#xdp-newbies)
    mailing list:
    -   [bpf.h and you…](https://www.spinics.net/lists/xdp-newbies/msg00179.html)
    -   [Contextually speaking…](https://www.spinics.net/lists/xdp-newbies/msg00181.html)
    -   [BPF Verifier Overview](https://www.spinics.net/lists/xdp-newbies/msg00185.html)
-   [A blog post series about eBPF from Ferris Ellis](https://ferrisellis.com/tags/ebpf/).
-   [List of BPF features per kernel version](https://github.com/iovisor/bcc/blob/master/docs/kernel-versions.md),
    in bcc repository.
-   [A BPF reference guide](https://github.com/iovisor/bcc/blob/master/docs/reference_guide.md)
    about BPF C and bcc Python helpers, from bcc repository.
-   [Making the Kernel’s Networking Data Path Programmable with BPF and XDP](http://schd.ws/hosted_files/ossna2017/da/BPFandXDP.pdf)
    (Daniel Borkmann, OSSNA17, Los Angeles, September 2017)
    A set of slides covering all the basics about eBPF and XDP (mostly for network processing).
-   [The BSD Packet Filter](https://speakerdeck.com/tuxology/the-bsd-packet-filter)
    (Suchakra Sharma, June 2017)
    An introduction mostly covering the tracing aspects.
-   [BPF: tracing and more](http://www.slideshare.net/brendangregg/bpf-tracing-and-more)
    (Brendan Gregg, January 2017)
    An introduction mostly covering the tracing aspects.
-   [Linux BPF Superpowers](http://www.slideshare.net/brendangregg/linux-bpf-superpowers)
    (Brendan Gregg, March 2016)
    An introduction mostly covering the tracing aspects, first part with flame
    graphs.
-   [IO Visor](https://www.socallinuxexpo.org/sites/default/files/presentations/Room%20211%20-%20IOVisor%20-%20SCaLE%2014x.pdf)
    (Brenden Blanco, SCaLE 14x, January 2016)
    Also introduces [IO Visor project](https://www.iovisor.org/).
-   [BPF — in-kernel virtual machine](https://events.linuxfoundation.org/sites/events/files/slides/bpf_collabsummit_2015feb20.pdf)
    (Alexei Starovoitov, February 2015)
    Presentation by the author of eBPF.
-   [Extending extended BPF](https://lwn.net/Articles/603983/)
    (Jonathan Corbet, July 2014).

### BPF Internals

-   Daniel Borkmann has made several presentations and papers covering the internals of eBPF, in particular about its use with tc.
    -   [eBPF and XDP walkthrough and recent updates](https://fosdem.org/2017/schedule/event/ebpf_xdp/)
        (fosdem17, Brussels, Belgium, February 2017).
    -   [Advanced programmability and recent updates with tc's cls_bpf](http://netdevconf.org/1.2/session.html?daniel-borkmann)
        (netdev 1.2, Tokyo, October 2016)
        Details on eBPF, its use for tunneling and encapsulation, direct packet access, and more.
    -   [cls_bpf/eBPF updates since netdev 1.1](http://netdevconf.org/1.2/slides/oct5/07_tcws_daniel_borkmann_2016_tcws.pdf)
        (netdev 1.2, Tokyo, October 2016, part of
        [this tc workshop](http://netdevconf.org/1.2/session.html?jamal-tc-workshop)).
    -   [On getting tc classifier fully programmable with cls_bpf](http://www.netdevconf.org/1.1/proceedings/slides/borkmann-tc-classifier-cls-bpf.pdf)
        (netdev 1.1, Sevilla, February 2016)
        Introduction to eBPF, including several features (map management, tail
        calls, verifier). The full paper
        [is also available here](http://www.netdevconf.org/1.1/proceedings/papers/On-getting-tc-classifier-fully-programmable-with-cls-bpf.pdf).
    -   [Linux tc and eBPF](https://archive.fosdem.org/2016/schedule/event/ebpf/attachments/slides/1159/export/events/attachments/ebpf/slides/1159/ebpf.pdf)
        (fosdem16, Brussels, Belgium, January 2016).
-   [IO Visor blog](https://www.iovisor.org/resources/blog).
-   [Linux Networking Explained](http://www.slideshare.net/ThomasGraf5/linux-networking-explained)
    (Thomas Graf, LinuxCon, Toronto, August 2016) Linux networking internals,
    with a part about eBPF.

### Kernel Tracing

-   [Meet-cute between eBPF and Kernel Tracing](http://www.slideshare.net/vh21/meet-cutebetweenebpfandtracing)
    (Viller Hsiao, July 2016)
    Kprobes, uprobes, ftrace
-   [Linux Kernel Tracing](http://www.slideshare.net/vh21/linux-kernel-tracing)
    (Viller Hsiao, July 2016)
    Systemtap, Kernelshark, trace-cmd, LTTng, perf-tool, ftrace, hist-trigger,
    perf, function tracer, tracepoint, kprobe/uprobe…
-   Brendan Gregg's blog, and in particular [Linux BPF Superpowers](http://www.brendangregg.com/blog/2016-03-05/linux-bpf-superpowers.html)
    article.

### XDP

-   [Work-in-progress documentation for XDP](https://prototype-kernel.readthedocs.io/en/latest/networking/XDP/index.html)
    started by Jesper Dangaard Brouer, meant to be a collaborative work;
    contributions welcome.
-   The [BPF and XDP Reference Guide](http://docs.cilium.io/en/latest/bpf/)
    from Cilium project.
-   [XDP overview](https://www.iovisor.org/technology/xdp) on the IO Visor
    website.
-   [eXpress Data Path (XDP)](https://github.com/iovisor/bpf-docs/raw/master/Express_Data_Path.pdf)
    (Tom Herbert, Alexei Starovoitov, March 2016)
    The first presentation about XDP.
-   [BoF - What Can BPF Do For You?](https://events.linuxfoundation.org/sites/events/files/slides/iovisor-lc-bof-2016.pdf)
    (Brenden Blanco, LinuxCon, Toronto, August 2016).
-   [eXpress Data Path](http://www.slideshare.net/IOVisor/express-data-path-linux-meetup-santa-clara-july-2016)
    (Brenden Blanco, Linux Meetup at Santa Clara, July 2016) Contains some benchmark results obtained with the mlx4 driver.
-   Jesper Dangaard Brouer has several sets of slides describing the internals
    of XDP:
    -   [XDP − eXpress Data Path, Intro and future use-cases](http://people.netfilter.org/hawk/presentations/xdp2016/xdp_intro_and_use_cases_sep2016.pdf)
        (September 2016)
        “Linux Kernel’s fight against DPDK”. Future plans (as of this
        writing) for XDP and comparison with DPDK.
    -   [Network Performance Workshop](http://netdevconf.org/1.2/session.html?jesper-performance-workshop)
        (netdev 1.2, Tokyo, October 2016)
        Additional hints about XDP internals and expected evolution.
    -   [XDP – eXpress Data Path, Used for DDoS protection](http://people.netfilter.org/hawk/presentations/OpenSourceDays2017/XDP_DDoS_protecting_osd2017.pdf)
        (OpenSourceDays, March 2017)
        Details and use cases about XDP, with benchmark results, and code
        snippets for benchmarking as well as for basic DDoS protection with
        eBPF/XDP (based on an IP blacklisting scheme).
    -   [Memory vs. Networking, Provoking and fixing memory bottlenecks](http://people.netfilter.org/hawk/presentations/MM-summit2017/MM-summit2017-JesperBrouer.pdf)
        (LSF Memory Management Summit, March 2017)
        Advanced details about current memory issues faced by XDP developers.
    -   [XDP for the Rest of Us](http://netdevconf.org/2.1/session.html?gospodarek)
        (netdev 2.1, Montreal, April 2017), with Andy Gospodarek.
        How to get started with eBPF and XDP for normal humans.
        Also summarized by Julia Evans on
        [her blog](http://jvns.ca/blog/2017/04/07/xdp-bpf-tutorial/).
-   [XDP workshop — Introduction, experience, and future development](http://netdevconf.org/1.2/session.html?herbert-xdp-workshop)
    (Tom Herbert, netdev 1.2, Tokyo, October 2016) (Video).
-   [High Speed Packet Filtering on Linux](https://cdn.shopify.com/s/files/1/0177/9886/files/phv2017-gbertin.pdf)
    (Gilberto Bertin, DEF CON 25, Las Vegas, July 2017) About packet filtering
    on Linux, DDoS protection, packet processing in the kernel, kernel bypass,
    XDP and eBPF.

### cBPF

-   [The BSD Packet Filter: A New Architecture for User-level Packet Capture](http://www.tcpdump.org/papers/bpf-usenix93.pdf)
    (Steven McCanne and Van Jacobson, 1992)
    The original paper about (classic) BPF.
-   [The FreeBSD manual page about BPF](http://www.gsp.com/cgi-bin/man.cgi?topic=bpf).
-   [Linux’ packet mmap(2), BPF, and Netsniff-NG](http://borkmann.ch/talks/2013_devconf.pdf)
    (Daniel Borkmann, 2013).
-   [tc and cls bpf: lightweight packet classifying with BPF](http://borkmann.ch/talks/2014_devconf.pdf)
    (Daniel Borkmann, 2013).
-   [Introducing Cloudflare's BPF Tools](https://blog.cloudflare.com/introducing-the-bpf-tools/)
    (Marek Majkowski, Cloudflare, 2014) Usage of BPF bytecode with the `xt_bpf`
    module for iptables.
-   [Libpcap filters syntax](http://biot.com/capstats/bpf.html).

### Hardware Offload

-   [eBPF/XDP hardware offload to SmartNICs](http://netdevconf.org/1.2/session.html?jakub-kicinski)
    (Jakub Kicinski and Nic Viljoen, netdev 1.2, Tokyo, October 2016)
    Hardware offload for eBPF with TC or XDP (Linux kernel 4.9+), introduced by
    Netronome.

## Projects based on, or related to eBPF

-   P4 has some interactions with eBPF:
    -   [P4 on the Edge](https://schd.ws/hosted_files/2016p4workshop/1d/Intel%20Fastabend-P4%20on%20the%20Edge.pdf)
        (John Fastabend, May 2016) P4 with eBPF to create high-performance
        programmable switches.
    -   [OvS Orbit episode (#11), called P4 on the Edge](https://ovsorbit.org/#e11),
        (August 2016), related to the former item. Audio interview of John
        Fastabend by Ben Pfaff, one of the core maintainers of Open vSwitch.
    -   [P4, EBPF and Linux TC Offload](https://open-nfp.org/m/documents/Open_NFP_P4_EBPF_Linux_TC_Offload_FINAL_5JHLETS.pdf)
        (Dinan Gunawardena and Jakub Kicinski, August 2016)
        P4 with some elements related to eBPF hardware offload on Netronome's
        NFP (Network Flow Processor) architecture.
    -   [Old documentation for P4 usage with eBPF](https://github.com/iovisor/bcc/tree/master/src/cc/frontends/p4),
        from bcc repository; deprecated by the P4_16 backend linked below.
    -   [P4_16 backend for eBPF](https://github.com/p4lang/p4c/blob/master/backends/ebpf/README.md).
-   Cilium project ([GitHub repository](https://github.com/cilium/cilium)) is a
    technology relying on BPF and XDP to provide “fast in-kernel networking and
    security policy enforcement for containers based on eBPF programs generated
    on the fly”. Many presentations available (with overlap):
    -   [Cilium: Networking & Security for Containers with BPF & XDP](http://www.slideshare.net/ThomasGraf5/clium-container-networking-with-bpf-xdp),
        also featuring a load balancer use case
        (Thomas Graf, Linux Plumbers conference, Santa Fe, November 2016)
    -   [Cilium: Networking & Security for Containers with BPF & XDP](http://www.slideshare.net/Docker/cilium-bpf-xdp-for-containers-66969823)
        (Thomas Graf, Docker Distributed Systems Summit, October 2016 —
        [video](https://www.youtube.com/watch?v=TnJF7ht3ZYc&list=PLkA60AVN3hh8oPas3cq2VA9xB7WazcIgs))
    -   [Cilium: Fast IPv6 container Networking with BPF and XDP](http://www.slideshare.net/ThomasGraf5/cilium-fast-ipv6-container-networking-with-bpf-and-xdp)
        (Thomas Graf, LinuxCon, Toronto, August 2016)
    -   [Cilium: BPF & XDP for containers](https://fosdem.org/2017/schedule/event/cilium/)
        (Thomas Graf, fosdem17, Brussels, Belgium, February 2017)
    -   [OvS Orbit episode (#4)](https://ovsorbit.benpfaff.org/) (May 2016)
        Interview of Thomas Graf by Ben Pfaff.
    -   [A generic introduction to Cilium](https://opensource.googleblog.com/2016/11/cilium-networking-and-security.html)
        (Daniel Borkmann, as a guest author on Google Open Source blog,
        November 2016).
    -   [A podcast by Ivan Pepelnjak](http://blog.ipspace.net/2016/10/fast-linux-packet-forwarding-with.html)
        by Ivan Pepelnjak interviewing Thomas Graf (October 2016) on eBPF, P4,
        XDP and Cilium.
-   Open vSwitch (OvS), and its related project Open Virtual Network
    (OVN, an open source network virtualization solution) are considering to use
    eBPF at various level:
    -   [Offloading OVS Flow Processing using eBPF](http://openvswitch.org/support/ovscon2016/7/1120-tu.pdf)
        (William (Cheng-Chun) Tu, OvS conference, San Jose, November 2016)
    -   [Coupling the Flexibility of OVN with the Efficiency of IOVisor](http://openvswitch.org/support/ovscon2016/7/1245-bertrone.pdf)
        (Fulvio Risso, Matteo Bertrone and Mauricio Vasquez Bernal, OvS
        conference, San Jose, November 2016)
-   [XDP in practice: integrating XDP in our DDoS mitigation pipeline](http://netdevconf.org/2.1/session.html?bertin)
    (Gilberto Bertin, netdev 2.1, Montreal, April 2017) Protection against DDoS with XDP at Cloudflare.
-   [Droplet: DDoS countermeasures powered by BPF + XDP](http://netdevconf.org/2.1/session.html?zhou)
    (Huapeng Zhou, Doug Porter, Ryan Tierney, Nikita Shirokov, netdev 2.1,
    Montreal, April 2017) Protection against DDoS with XDP at Facebook.
-   [CETH for XDP](http://www.slideshare.net/IOVisor/ceth-for-xdp-linux-meetup-santa-clara-july-2016)
    (Yan Chan and Yunsong Lu, Linux Meetup, Santa Clara, July 2016)
    Common Ethernet Driver Framework for faster network I/O,
    a technology initiated by Mellanox.
-   [The VALE switch](http://info.iet.unipi.it/~luigi/vale/) has
    [a BPF extension module](https://github.com/YutaroHayakawa/vale-bpf).
-   Suricata, an open source intrusion detection system,
    [relies on eBPF components](https://www.stamus-networks.com/2016/09/28/suricata-bypass-feature/)
    for its “capture bypass” features:
    -   [The adventures of a Suricate in eBPF land](http://netdevconf.org/1.2/slides/oct6/10_suricata_ebpf.pdf)
        (Éric Leblond, netdev 1.2, Tokyo, October 2016)
    -   [eBPF and XDP seen from the eyes of a meerkat](https://www.slideshare.net/ennael/kernel-recipes-2017-ebpf-and-xdp-eric-leblond)
        (Éric Leblond, Kernel Recipes, Paris, September 2017)
-   [InKeV: In-Kernel Distributed Network Virtualization for DCN](https://github.com/iovisor/bpf-docs/blob/master/university/sigcomm-ccr-InKev-2016.pdf)
    (Z. Ahmed, M. H. Alizai and A. A. Syed, SIGCOMM, August 2016)
-   [gobpf - utilizing eBPF from Go](https://fosdem.org/2017/schedule/event/go_bpf/)
    (Michael Schubert, fosdem17, Brussels, Belgium, February 2017)
    A “library to create, load and use eBPF programs from Go”
-   [ply](https://wkz.github.io/ply/) A small but flexible open source
    dynamic tracer for Linux, with features similar to the bcc tools,
    but with a simpler language inspired by awk and dtrace.

## Tutorials

Brendan Gregg has produced excellent tutorials intended for people who want
to use bcc tools for tracing and monitoring events in the kernel.
[The first tutorial about using bcc itself](https://github.com/iovisor/bcc/blob/master/docs/reference_guide.md)
comes with eleven steps (as of today) to understand how to use the existing
tools, while
[the one intended for Python developers](https://github.com/iovisor/bcc/blob/master/docs/tutorial_bcc_python_developer.md)
focuses on developing new tools, across seventeen “lessons”.

Sasha Goldshtein also has some
[Linux Tracing Workshops Materials](https://github.com/goldshtn/linux-tracing-workshop)
involving the use of several BPF tools for tracing.

Another post by Jean-Tiare Le Bigot provides a detailed (and instructive!)
example of
[using perf and eBPF to setup a low-level tracer](https://blog.yadutaf.fr/2017/07/28/tracing-a-packet-journey-using-linux-tracepoints-perf-ebpf/)
for ping requests and replies

Few tutorials exist for network-related eBPF use cases. There are some
interesting documents, including an eBPF Offload Starting Guide, on the
[Open NFP](https://open-nfp.org/dataplanes-ebpf/technical-papers/) platform
operated by Netronome. Other than these, the talk from Jesper,
[XDP for the Rest of Us](http://netdevconf.org/2.1/session.html?gospodarek),
is probably one of the best ways to get started with XDP.

## Examples

It is always nice to have examples. To see how things really work. But BPF
program samples are scattered across several projects, so I listed all the ones
I know of. The examples do not always use the same helpers (for instance, tc
and bcc both have their own set of helpers to make it easier to write BPF
programs in C language).

### From the kernel

The kernel contains examples for most types of program: filters to bind to
sockets or to tc interfaces, event tracing/monitoring, and even XDP. You can
find these examples under the
[linux/samples/bpf/](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/samples/bpf)
directory.

Also do not forget to have a look to the logs related to the (git) commits that
introduced a particular feature, they may contain some detailed example of the
feature. You can search the logs in many places, such as on
[git.kernel.org](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git),
[on GitHub](https://github.com/torvalds/linux), or on your local
repository if you have cloned it. If you are not familiar with git, try things
like `git blame <file>` to see what commit introduced a particular line of
code, then `git show <commit>` to have details (or search by keyword in `git
log` results, but this may be tedious). See also [the list of eBPF features per
kernel version][kernfeatures] on bcc repository, that links to relevant
commits.

### From package iproute2

The iproute2 package provide several examples as well. They are obviously
oriented towards network programming, since the programs are to be attached to
tc ingress or egress interfaces. The examples dwell under the
[iproute2/examples/bpf/](https://git.kernel.org/cgit/linux/kernel/git/shemminger/iproute2.git/tree/examples/bpf)
directory.

### From bcc set of tools

Many examples are [provided with bcc](https://github.com/iovisor/bcc/tree/master/examples):

-   Some are networking example programs, under the associated directory. They
    include socket filters, tc filters, and a XDP program.

-   The `tracing` directory include a lot of example tracing programs. The
    tutorials mentioned earlier are based on these. These programs cover a wide
    range of event monitoring functions, and some of them are
    production-oriented. Note that on certain Linux distributions (at least for
    Debian, Ubuntu, Fedora, Arch Linux), these programs have been
    [packaged](https://github.com/iovisor/bcc/blob/master/INSTALL.md) and can be
    “easily” installed by typing e.g. `# apt install bcc-tools`, but as of this
    writing (and except for Arch Linux), this first requires to set up IO Visor's
    own package repository.

-   There are also some examples using Lua as a different BPF back-end (that
    is, BPF programs are written with Lua instead of a subset of C, allowing to
    use the same language for front-end and back-end), in the third directory.

### Manual pages

While bcc is generally the easiest way to inject and run a BPF program in the
kernel, attaching programs to tc interfaces can also be performed by the `tc`
tool itself. So if you intend to use BPF with tc, you can find some example
invocations in the
[`tc-bpf(8)` manual page](http://man7.org/linux/man-pages/man8/tc-bpf.8.html).

## The Code

Sometimes, BPF documentation or examples are not enough, and you may have no
other solution that to display the code in your favorite text editor (which
should be Vim of course) and to read it. Or you may want to hack into the code
so as to patch or add features to the machine. So here are a few pointers to
the relevant files, finding the functions you want is up to you!

### BPF core

-   The file
    [linux/include/linux/bpf.h](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/include/linux/bpf.h)
    and its counterpart
    [linux/include/uapi/bpf.h](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/include/uapi/linux/bpf.h)
    contain definitions related to eBPF, to be used respectively in the
    kernel and to interface with userspace programs.

-   On the same pattern, files
    [linux/include/linux/filter.h](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/include/linux/filter.h)
    and
    [linux/include/uapi/filter.h](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/include/uapi/linux/filter.h)
    contain information used to run the BPF programs.

-   The main pieces of code related to BPF are under
    [linux/kernel/bpf/](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/kernel/bpf)
    directory. The different operations permitted by the system call, such as
    program loading or map management, are implemented in file `syscall.c`, while
    `core.c` contains the interpreter. The other files have self-explanatory
    names: `verifier.c` contains the verifier (no kidding), `arraymap.c` the
    code used to interact with maps of type array, and so on.

-   The helpers, as well as several functions related to networking (with tc,
    XDP…) and available to the user, are implemented in
    [linux/net/core/filter.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/net/core/filter.c).
    It also contains the code to migrate cBPF bytecode to eBPF (since all cBPF
    programs are now translated to eBPF in the kernel before being run).


-   The JIT compilers are under the directory of their respective
    architectures, such as file
    [linux/arch/x86/net/bpf_jit_comp.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/arch/x86/net/bpf_jit_comp.c)
    for x86.

-   You will find the code related to the BPF components of tc in the
    [linux/net/sched/](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/net/sched)
    directory, and in particular in files `act_bpf.c` (action) and `cls_bpf.c`
    (filter).

-   I have not hacked with event tracing in BPF, so I do not really know
    about the hooks for such programs. There is some stuff in
    [linux/kernel/trace/bpf_trace.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/kernel/trace/bpf_trace.c).
    If you are interested in this and want to know more, you may dig on the side
    of Brendan Gregg's presentations or blog posts.

-   Nor have I used seccomp-BPF. But the code is in
    [linux/kernel/seccomp.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/kernel/seccomp.c),
    and some example use cases can be found in
    [linux/tools/testing/selftests/seccomp/seccomp_bpf.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/tools/testing/selftests/seccomp/seccomp_bpf.c).

### XDP hooks code

Once loaded into the in-kernel BPF virtual machine, XDP programs are hooked
from userspace into the kernel network path thanks to a Netlink command. On
reception, the function `dev_change_xdp_fd()` in file
[linux/net/core/dev.c](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/net/core/dev.c)
is called and sets a XDP hook. Such hooks are located in the drivers of
supported NICs. For example, the mlx4 driver used for some Mellanox hardware
has hooks implemented in files under the
[drivers/net/ethernet/mellanox/mlx4/](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/net/ethernet/mellanox/mlx4/)
directory. File en_netdev.c receives Netlink commands and calls
`mlx4_xdp_set()`, which in turns calls for instance `mlx4_en_process_rx_cq()`
(for the RX side) implemented in file en_rx.c.

## Tools and utilities

### bcc

-   [bcc](https://github.com/iovisor/bcc/) framework and set of tools - One way
    to handle BPF programs, in particular for tracing and monitoring. Also
    includes some utilities that may help inspect maps or programs on the
    system.
-   [P4 compiler for BPF targets](https://github.com/iovisor/bcc/tree/master/src/cc/frontends/p4/compiler)
    for bcc - An alternative to the restricted C.
-   [Lua front-end](https://github.com/iovisor/bcc/tree/master/src/lua) for
    bcc - Another alternative to C, and even to most of the Python code used in
    bcc.

### iproute2

-   [iproute2](https://git.kernel.org/pub/scm/network/iproute2/iproute2.git) -
    Package containing tools for network management on Linux. In particular, it
    contains `tc`, used to manage eBPF filters and actions, and `ip`, used to
    manage XDP programs. Most of the code related to BPF is in lib/bpf.c.
-   [iproute2-next](https://git.kernel.org/pub/scm/network/iproute2/iproute2-next.git) -
    The development tree, synchronised with net-next.

### LLVM

-   [LLVM](https://llvm.org/) package contains several tools used in eBPF
    workflow. Snapshots of the latest versions for Ubuntu/Debian can be
    retrieved from [here](http://apt.llvm.org/).
    -   clang is used to compile C to eBPF object file under the ELF format
        (clang v3.7.1+). The BPF backend was added with
        [this commit](https://reviews.llvm.org/D6494).
    -   llvm-objdump is used to dump the content of an object file in
        human-readable format, possibly with the initial C source code
        (llvm-objdump v4.0+).
    -   llvm-mc is used to compile from LLVM intermediate representation to
        eBPF object file, so that one can compile from C to eBPF assembly,
        tinker with assembly, then compile to ELF file.

### bpftool and others from the kernel tree

-   [bpftool](https://git.kernel.org/pub/scm/linux/kernel/git/bpf/bpf-next.git/tree/tools/bpf/bpftool)
    and other tools in the kernel tree, under
    [linux/tools/net/](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/tools/net?h=v4.14)
    for versions earlier than 4.15, or
    [linux/tools/bpf/](https://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next.git/tree/tools/bpf)
    after that:
    -   `bpftool` - A generic utility that can be used to interact with eBPF
        programs and maps from userspace, for example to show, dump, load,
        disassemble, pin programs, or to show, create, pin, update, delete
        maps, or to attach and detach programs to cgroups.
    -   `bpf_asm` - A minimal cBPF assembler.
    -   `bpf_dbg` - A small debugger for cBPF programs.
    -   `bpf_jit_disasm` - A disassembler for both BPF flavors and could be
        highly useful for JIT debugging.

### User space eBPF

-   [uBPF](https://github.com/iovisor/ubpf/) - Written in C. Contains an
    interpreter, a JIT compiler for x86_64 architecture, an assembler and a
    disassembler.
-   [A generic implementation](https://github.com/YutaroHayakawa/generic-ebpf) -
    With support for FreeBSD kernel, FreeBSD user space, Linux kernel, Linux
    user space and MacOSX user space. Used for the [BPF extension module for
    VALE switch](https://github.com/YutaroHayakawa/vale-bpf).
-   [rbpf](https://github.com/qmonnet/rbpf) - Written in Rust. Interpreter for
    Linux, MacOSX and Windows, and JIT-compiler for x86_64 under Linux.

### Testing in virtual environments

-   [A Vagrant setup](https://github.com/iovisor/xdp-vagrant) - To easily test
    XDP. Less useful now that generic XDP (driver-independant, mostly for
    testing) exists.
-   [bcc in a Docker container](https://github.com/zlim/bcc-docker).

## Development and Community

-   [The bpf-next tree](https://git.kernel.org/pub/scm/linux/kernel/git/bpf/bpf-next.git/) -
    BPF patches land in this tree. It is regularly merged into
    [net-next](https://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next.git),
    which is itself merged for each release to Linus' tree.
-   [Kernel documentation](https://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next.git/tree/Documentation/bpf/bpf_devel_QA.txt)
    about contributions to BPF.
-   [The netdev mailing list](http://lists.openwall.net/netdev/) - Mailing list
    for Linux kernel networking stack development. All patches are sent there
    for review and inclusion.
-   [XDP-newbies](http://vger.kernel.org/vger-lists.html#xdp-newbies) - A
    mailing list specially dedicated to XDP programming (both for architecture
    or for asking for help).
-   [IO Visor mailing list](http://lists.iovisor.org/pipermail/iovisor-dev/) -
    BPF is at the heart of the project, and is regularly discussed on the
    mailing list.
-   [@IOVisor Twitter account](https://twitter.com/IOVisor).

## Other lists of resources on eBPF

-   [IO Visor's bcc documentation](https://github.com/iovisor/bcc/tree/master/docs)
-   [IO Visor's bpf-docs repository](https://github.com/iovisor/bpf-docs/)
-   [Dive into BPF: A List of Reading Material](https://qmonnet.github.io/whirl-offload/2016/09/01/dive-into-bpf/)

## Acknowledgement

Thank you to Quentin Monnet and Daniel Borkmann for their original work on [Dive into BPF: A List of Reading Material](https://qmonnet.github.io/whirl-offload/2016/09/01/dive-into-bpf/) which became the basis for this list.

## Contribute

Contributions welcome! Read the [contribution guidelines](contributing.md) first.

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law, zoidbergwill has waived all copyright and
related or neighboring rights to this work.
