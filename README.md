# dotnet-node-python-openjdk-tools-docker

A polyglot developer container with **.NET, Node.js, Python, and OpenJDK** tooling for modern development environments.

---

## 📦 Docker Image Features
1. .NET SDK 10 (RC2)
2. Node.js 22.x with latest npm
3. Python 3.x with pip, setuptools, wheel
4. OpenJDK 21 for Java development
5. Secure non-root `appuser`
6. Clean, lean image following Docker best practices

---

## 🚀 Build the Docker Image

Clone the repository and build the image using the provided Dockerfile:

```bash
# Clone repo
git clone https://github.com/vaibhav-gawali/dotnet-node-python-openjdk-tools-docker.git
cd dotnet-node-python-openjdk-tools-docker
```

# Build image
```bash
docker build -t dotnet-node-python-openjdk:latest -f DockerFiles/Dockerfile .
```
## 🏃 Run the Container

```bash
docker run -it --rm dotnet-node-python-openjdk:latest bash
```

Mount your local workspace:

```bash
docker run -it --rm -v $(pwd):/workspace dotnet-node-python-openjdk:latest bash
```

## 🔧 Verify Installations
Inside the container, check installed runtimes:

```bash
dotnet --version
node --version
npm --version
python3 --version
java -version
```

## 📖 Notes
1. Default working directory: /workspace
2. Runs as non-root user: appuser

## 📜 License
This project is licensed under the MIT License.
All packages included in this Docker image are subject to their respective licensing terms.

---

## 📚 References

| Sr. No. | Reference   | Links                                                                | Comments                         |
| ------- | ----------- | --------------------------------------------------------------------- | -------------------------------- |
| 1       | **.NET**    | [Official Documentation](https://learn.microsoft.com/dotnet/)<br>[GitHub Repository](https://github.com/dotnet)<br>[Docker Hub Images](https://hub.docker.com/_/microsoft-dotnet)      | For learning and reference.<br>To view source and contribute.<br>For available .NET Docker images. |
| 2       | **Node.js** | [Official Documentation](https://nodejs.org/en/docs/)<br>[GitHub Repository](https://github.com/nodejs/node)<br>[Docker Hub Images](https://hub.docker.com/_/node)                 | For Node.js API and guides.<br>To view source and contribute.<br>For available Node.js Docker images. |
| 3       | **Ubuntu (Base OS)** | [Official Documentation](https://ubuntu.com/)<br>[GitHub Repository](https://github.com/canonical/ubuntu.com)<br>[Docker Hub Images](https://hub.docker.com/_/ubuntu)                 | For Ubuntu usage and features.<br>To view Ubuntu's source and contribute.<br>For available Ubuntu Docker images. |
| 4       | **Python**  | [Official Documentation](https://docs.python.org/3/)<br>[GitHub Repository](https://github.com/python/cpython)<br>[Docker Hub Images](https://hub.docker.com/_/python)                | For Python language and library details.<br>To view source and contribute.<br>For available Python Docker images. |
| 5       | **OpenJDK** | [Official Documentation](https://openjdk.org/)<br>[GitHub Repository](https://github.com/openjdk/jdk)<br>[Docker Hub Images](https://hub.docker.com/_/openjdk)              | For OpenJDK features and guidelines.<br>To view source and contribute.<br>For available OpenJDK Docker images. |
