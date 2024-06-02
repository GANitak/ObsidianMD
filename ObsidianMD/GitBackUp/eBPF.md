https://isovalent.com/books/ebpf/ by Liz Rice

6:33pm
# Application Components

Here is an overview of the `jobs-app` components:

- `coreapi` is a RESTful HTTP main API used by the `resumes`, `recruiter`, and `jobposting` components. It manages creating, retrieving and listing resumes and jobpostings from Elasticsearch.
    
- `crawler` will periodically generate random resumes and sends them to `loader` via gRPC.
    
- `loader` is a gRPC service which submits resumes into the resumes kafka topic to be processed by the `resumes` component.
    
- `resumes` subscribes to the resumes kafka topic, and submits the resumes to the `coreapi`, which stores them in Elasticsearch.
    
- `elasticsearch` used to store resumes, job postings, and analytics.
    
- `kafka` takes resumes in from `loader` in the resumes topic.
    
- `jobposting` uses the `coreapi` to lists job postings on a web UI and allows applicants to submit their resumes.
    
- `recruiter` uses the `coreapi` to list applicants and allows you to view their resumes.

2 These and other details come from Alexei Starovoitov’s 2015 NetDev presentation, “BPF – in-kernel virtual machine”.
filters, which are programs written to determine whether to accept or reject a network packet. These programs were written in the BPF instruction set, a general-purpose set of 32-bit instructions that closely resembles assembly language. Here’s an example taken directly from that paper:
```code.bpf=
ldh [12]
jeq #ETHERTYPE IP, L1, L2
L1: ret #TRUE
L2: ret #0
```
**ldh**: This stands for "load half-word".
**jeq**: This stands for "jump if equal"