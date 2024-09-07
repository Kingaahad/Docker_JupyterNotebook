🐳 Setting Up Jupyter Notebook with Docker

This guide walks you through creating a **Dockerfile** for setting up and running a Jupyter Notebook inside a Docker container. 🧑‍💻

---

🚀 Step 01 - Create a Dockerfile
Start by creating a `Dockerfile` in **VS Code** with the following code:

```dockerfile
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

🌐 Access Jupyter Notebook

- Open your browser and type the following URL:
  
  `http://localhost:8888`

- You should now see the Jupyter Notebook interface running in your browser.

---


🎨 Cool Enhancements
- Customize your environment further by adding libraries or extensions to your Dockerfile.
- Add volume mounting to save your work outside the container:

```dockerfile
VOLUME ["/usr/src/app"]
```

--- 

That's it! 🎉 You've successfully set up **Jupyter Notebook** in a Docker container. Happy coding!

---

