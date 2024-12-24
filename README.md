# Openproject_RLS
## OpenProject (All-in-One) Setup Using Docker in GitHub Codespaces

This guide explains how to set up and run an OpenProject all-in-one container using Docker in GitHub Codespaces.

---

### Prerequisites
- A GitHub repository where you can launch a Codespace.
- Basic knowledge of terminal commands.

---

### Step 1: Set up GitHub Codespace
1. Navigate to your GitHub repository.
2. Open a Codespace by clicking **Code** > **Codespaces** > **Create Codespace on main**.

---

### Step 2: Install Docker CLI and dependencies
1. Open the terminal in your Codespace.
2. Install Docker CLI and dependencies:
   ```bash
   sudo apt-get update
   sudo apt-get install -y docker.io
   ```
3. Verify the installation:
   ```bash
   docker --version
   ```

---

### Step 3: Clone the OpenProject repository
1. Clone the official OpenProject Docker repository:
   ```bash
   git clone https://github.com/opf/openproject-deploy --depth=1
   cd openproject-deploy/docker-compose
   ```

---

### Step 4: Modify the Docker Compose file (Optional)
You can update the default configuration in `docker-compose.yml` if necessary.

#### Example:
To map a custom port:
```yaml
services:
  openproject:
    ports:
      - "8080:80"  # Maps port 8080 on your machine to port 80 in the container
```

---

### Step 5: Start OpenProject
1. Start the container using:
   ```bash
   docker-compose up
   ```
2. Wait for the logs to confirm OpenProject is running.

---

### Step 6: Access OpenProject
1. In GitHub Codespaces, open the **Ports** tab.
2. Forward port `8080` (or the port you configured).
3. Open the forwarded URL in your browser.

---

### Step 7: Persist data using volumes (Optional)
To retain data across sessions, modify the `volumes` section in `docker-compose.yml`:

```yaml
services:
  openproject:
    volumes:
      - openproject_data:/var/openproject/assets
volumes:
  openproject_data:
```

---

### Step 8: Stop and clean up
1. To stop the container, use:
   ```bash
   docker-compose down
   ```
2. To remove Docker resources:
   ```bash
   docker system prune -a
   ```

---

### Summary
You now have a running OpenProject instance in GitHub Codespaces using Docker. You can experiment with OpenProject or extend its functionality further.

---

#### Notes:
- Use the `docker-compose.yml` file to manage configurations.
- Make sure to persist data if needed for production usage.
