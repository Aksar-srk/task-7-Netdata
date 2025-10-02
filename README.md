# TASK 7: Monitor System Resources Using Netdata

## 📌 Objective
Install and run **Netdata** to visualize system and application performance metrics in real-time.

---

## 🛠️ Tools Used
- **Netdata** → Free, open-source monitoring tool for real-time metrics.  
- **Docker** → To run Netdata as a container.  

---

## 📖 What is Netdata?
Netdata is a **lightweight, real-time monitoring and troubleshooting tool** for servers, containers, applications, and networks. It provides beautiful dashboards with interactive charts for CPU, memory, disk, network, and container usage.

---

## ⚡ Steps Performed

## 1: Verify Docker Installation

Check Docker version:

```bash
docker --version
```

## 2. Build and Run Your Docker Image
```bash
docker build -t swiggy-app .
docker run -d -p 3000:80 --name swiggy-clone swiggy-clone
```
- -p 3000:80 → maps container’s Nginx port (80) to your local http://localhost:3000
```bash
docker ps
```
- to show your swiggy-clone container running.
-  Then open 👉 http://localhost:3000
 [AWS EC2 Security Group](images/page.png)

## 3. Add Netdata for Monitoring
```bash
docker run -d --name=netdata `
  -p 19999:19999 `
  --pid=host `
  --cap-add SYS_PTRACE `
  --security-opt apparmor=unconfined `
  -e NETDATA_CLOUD_DISABLE=1 `
  -v /proc:/host/proc:ro `
  -v /sys:/host/sys:ro `
  -v /var/run/docker.sock:/var/run/docker.sock `
  netdata/netdata
 ```
- Run
 ```
docker ps
```
- show both swiggy-clone and netdata running.
  [AWS EC2 Security Group](images/page.png)
- Then open 👉 http://localhost:19999

## 4.Access Local Dashboard

- Once the container is running, open:
👉 http://localhost:19999
- Now you should see the classic Netdata dashboard with a sidebar menu:
  [AWS EC2 Security Group](images/page.png)
- System → CPU
- System → Memory
- System → Disks
- System → Network
- Containers
- Screenshot 1 → CPU usage
[AWS EC2 Security Group](images/page.png)
- Screenshot 2 → Memory usage
 [AWS EC2 Security Group](images/page.png)
- Screenshot 3 → Docker Container metrics
 [AWS EC2 Security Group](images/page.png)
- Screenshot 4 → Network activity
 [AWS EC2 Security Group](images/page.png)
- Screenshot 5 → Health
 [AWS EC2 Security Group](images/page.png)
- Screenshot 6 → Stopping containers
 [AWS EC2 Security Group](images/page.png)

## 🧹 Cleanup Commands

After exploring Netdata, we stopped and removed the running containers to free system resources.

```bash
# Stop the Netdata container
docker stop netdata

# Remove the Netdata container
docker rm netdata

# Stop the Swiggy-clone container
docker stop swiggy-clone

# Remove the Swiggy-clone container
docker rm swiggy-clone
```
