# Caddy_Doc

## Here's a step-by-step guide on setting up and running Caddy server:

### 1. Downloading Caddy:
- Visit the [official Caddy download page](https://caddyserver.com/download) and download the appropriate version for your operating system.
  
### 2. Setting up Environment Variables:
- Once downloaded, extract the Caddy binary to a folder. Let's say you put it in `F:\caddy`.
- Add the folder path to your system's `PATH` environment variable. This allows you to run Caddy commands from any location in the Command Prompt.

### 3. Configuring Caddy:
- Inside the `F:\caddy` (example) folder, create a file named `Caddyfile`. This will be Caddy's configuration file.
- There should be no specific extension
- In the `Caddyfile`, add the following to set up a basic server:

   ```
  localhost

  reverse_proxy http://your_backend_server_address_here
  ```
 ## Example of Caddy config file 
  - In this example i have my static files in F:\caddy folder change your path accordingly
  ```
   {
    local_certs
  }

  http://localhost:8081
  {
    root * F:\caddy  
    file_server
  }
  https://localhost:4444
  {
    root * F:\caddy  
    file_server
    tls internal
  }
  ```
### 4. Checking for Port Conflicts:
- Before running Caddy, ensure that port 80 and 443 are free. You can check this by using:

   ```
  netstat -aon | findstr ":80"
  netstat -aon | findstr ":443"
  ```
- If you see other applications using these ports, especially `0.0.0.0:80` or `0.0.0.0:443`, you'll need to stop or reconfigure those applications. A common culprit is IIS (Windows' built-in web server). If you're not using IIS, you can disable it to free up the ports.

### 5. Running Caddy:
- Open a Command Prompt with administrative privileges.
- Navigate to the Caddy directory using `cd F:\caddy`.
- Run Caddy using the command: `caddy run`.

### 6. Accessing your Site:
- After running Caddy, open a web browser and navigate to `http://localhost`.
- If everything is set up correctly, your backend server's content will be displayed.

### 7. Stopping Caddy:
- To stop Caddy, you can simply press `Ctrl + C` in the Command Prompt where it's running.
