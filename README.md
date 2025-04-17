
# Monitoring System Resources Using Netdata


# what is Netdata?

Netdata is a free, open-source, real-time performance and health monitoring tool designed for systems and applications. It provides detailed, interactive dashboards to visualize metrics like CPU, memory, disk, network, and more, with minimal configuration and low overhead.
Key Features:
Real-Time Monitoring: Collects and displays metrics at a per-second granularity.

Comprehensive Metrics: Tracks system resources (CPU, RAM, disk I/O), network activity, Docker containers, and application performance.

Web Dashboard: Accessible via a browser (e.g., http://localhost:19999 when running locally), offering interactive charts and visualizations.

Alerting: Built-in health checks with configurable alerts for anomalies (e.g., high CPU usage).

Lightweight: Runs efficiently on servers, containers, or IoT devices.

Extensible: Supports plugins for monitoring databases, web servers, and custom apps.

Docker Support: Easily deployed via Docker for quick setup.



# Step 1: Installing Docker

Open terminal and install docker

# Step 2: Install Netdata via Docker

Run the following command to start Netdata in a Docker container:


```bash
  docker run -d --name=netdata -p 19999:19999 -v netdata:/etc/netdata -v /proc:/host/proc:ro -v /sys:/host/sys:ro --cap-add SYS_PTRACE --security-opt apparmor=unconfined netdata/netdata
```
This maps port 19999 for accessing, mounts necessary host directories for system metrics, and grants required permissions.

# Step 3: Accessing Netdata Dashboard

1. Open a web browser and navigate to:

```bash
http://localhost:19999
```

2. We  will see the Netdata dashboard displaying real-time metrics for CPU, memory, disk, network, and more.

   
![IMG_20250417_181348](https://github.com/user-attachments/assets/1cb9ede4-64f7-4698-b955-db002b1dd739)


# Step 4: Monitor Key Metrics

CPU: View usage by core, interrupts, and processes under the "CPU" section.

Memory: Check RAM, swap, and memory allocation in the "Memory" section.

Disk: Monitor disk I/O, utilization, and space in the "Disk" section.

Docker Containers:The Docker containers are running, so Netdata auto-detects and displays container metrics under "Containers."


# Step 5: Exploring Alerts and Logs

Alerts: Check the "Alarms" section in the dashboard for active alerts (e.g., high CPU or low disk space).


![IMG_20250417_181310](https://github.com/user-attachments/assets/a35aad9c-6e75-4d04-9b2f-d3ed78beca68)


![IMG_20250417_181328](https://github.com/user-attachments/assets/ea872a0d-5cb7-463f-80c3-c64c1b04ea02)



Logs: View Netdata logs for debugging or performance insights:

```bash
docker exec -it netdata cat /var/log/netdata/error.log
```

Logs are stored in /var/log/netdata/ inside the container.


![IMG_20250417_181415](https://github.com/user-attachments/assets/dcc33d8d-6118-4f8d-a5cd-65175febcb0c)


![IMG-20250417-WA0037](https://github.com/user-attachments/assets/4a1e2f1d-0423-4b1f-8b82-521464a9c92b)



# Step 6: Capturing  Dashboard Screenshot

On the Netdata dashboard, navigate to a view showing key metrics (e.g., CPU, memory, disk)


![IMG-20250417-WA0031](https://github.com/user-attachments/assets/9a415627-8cd1-497f-b678-f1a7616b8a5c)


###  Notes


If the dashboard doesn’t load, verify the Docker container is running:

```bash
docker ps
```


Check for errors in logs if metrics are missing

```bash
docker logs netdata
```


To stop the container

```bash
docker stop netdata
```






































    
