🐳 Setting Up Jupyter Notebook with Docker

This guide walks you through creating a Dockerfile for setting up and running a Jupyter Notebook inside a Docker container. 🧑‍💻

---

🚀 Step 01 - Create a Dockerfile
Start by creating a `Dockerfile` in **VS Code** with the following code:

```docker file
# Use an official Python runtime as a parent image
FROM python:3.12

# Set the working directory in the container
WORKDIR /usr/src/app

# Install Jupyter
RUN pip install notebook

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Expose port 8888 to the outside world
EXPOSE 8888

# Command to run Jupyter Notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
```

📂 Explanation of the Dockerfile:

- `FROM python:3.12`: Pulls an official Python 3.12 image from Docker Hub.  
- `WORKDIR /usr/src/app`: Sets the working directory inside the container.
- `RUN pip install notebook`: Installs Jupyter Notebook inside the container.
- `COPY . .`: Copies all files from the current directory to the container.
- `EXPOSE 8888`: Opens port 8888, so Jupyter is accessible externally.
- `CMD`: This command launches Jupyter Notebook when the container starts.

---

🛠️ Step 02 - Run the Devcontainer

1. **Open your terminal in VS Code**.
2. Click on the **"+"** icon to create a new terminal.
3. Run the following command:

```bash
jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser --allow-root
```

🔑 Step 03 - Setup Password
After launching Jupyter Notebook, you must retrieve the token and set a password.

Retrieve the Token by running this command in the terminal:

bash
Copy code
jupyter server list
This will display something like:

bash
Copy code
Currently running servers:
http://localhost:8888/?token=your_token_here :: /usr/src/app
Copy the Token and open the Jupyter Notebook interface at:

http://localhost:8888

Could you paste the token into the login prompt to access Jupyter Notebook for the first time?

Once logged in, you can set a password within the Jupyter interface by going to:

File Menu > Security Settings > Set Password
Use the password for future logins instead of the token.

🌐 Access Jupyter Notebook
After setting the password, you can access your Jupyter Notebook by navigating to:

http://localhost:8888

Use your password for secure access.

📸 Preview

Add a screenshot of the running Jupyter Notebook inside Docker.

🎨 Cool Enhancements
Customize your environment further by adding libraries or extensions to your Dockerfile.
Add volume mounting to save your work outside the container:
docker file
Copy code
VOLUME ["/usr/src/app"]

That's it! 🎉 You've successfully set up Jupyter Notebook in a Docker container and secured it with a password. Happy coding!
