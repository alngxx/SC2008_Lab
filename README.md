# SC2008 (Computer Network) - Lab 4

## Overview

This lab analyzes network traffic using **sFlow data** to identify top talkers, listeners, communication pairs, application protocols, and total traffic volume. It uses Python libraries to clean, process, and visualize flow records collected from campus or simulated networks.

## Features

* **Top Talkers & Listeners:** Determine the most active sending and receiving IPs.
* **Application Protocols:** Map port numbers to standard services (HTTP, HTTPS, etc.).
* **Traffic Calculation:** Estimate total traffic from IP packet sizes (in bytes) with sampling adjustment.
* **Network Visualization:** Display IP-to-IP communication with edge thickness proportional to packet counts and directional arrows.

## Tools & Libraries

```bash
pip install pandas matplotlib networkx ipwhois
```

* **pandas** → data preprocessing and analysis
* **matplotlib** → visualization and graph plotting
* **networkx** → building directed communication graphs
* **ipwhois** → organization lookup for IP addresses

## Workflow Summary

1. **Load & Clean Data:** Import CSV and label columns based on sFlow structure.
2. **Identify Active IPs:** Count occurrences of source and destination addresses.
3. **Map Application Ports:** Associate common ports with service types.
4. **Compute Total Traffic:**

   ```python
   total_traffic = sum(log_df['IP_size']) / (2**20) * log_df['sampling_rate'].iloc[0]
   ```

   Here, `IP_size` is in **bytes**, converted to **MB**, and scaled by the sampling rate (e.g., 2048).
5. **Visualize Network:** Generate a directed graph showing communication intensity and flow direction between IP hosts.


## Summary

* **Top Traffic Sources:** NTUNET1, NUSNET, NAS-NET, and A-STAR-AS-AP
* **Estimated Traffic Volume:** ~20 MB (scaled to ~40 GB with sampling)
* **Observation:** Few dominant flows represent the majority of total traffic, showing strong inter-institutional and cloud-based activity.


## Visualization

* **Nodes:** Represent IP hosts (equal size for clarity).
* **Edges:** Direction = data flow, width = packet count.
* **Colors:** Teal–purple gradient for unique identity.
* **Edge Labels:** Show number of packets exchanged.


## Conclusion

This lab demonstrates how traffic data can be analyzed programmatically to reveal communication patterns in large-scale networks. The visual and statistical insights support better understanding of dominant nodes and link behaviors.

**Author:** An Loc Nguyen

**Course:** SC2008 – Data Communication and Networking

**Institution:** Nanyang Technological University (NTU), Singapore

**Semester:** AY2025/26

