A polyglot developer container that brings together .NET SDK, Node.js, Python, and OpenJDK in a single, ready‑to‑use environment. Designed for developers who need a unified workspace for building cross‑platform applications, experimenting with hybrid workloads (.NET, Pyton, Node, Android SDK, OpenJDK, MAUI, Blazor), or running AI tooling alongside traditional runtimes.

This repository focuses on core runtimes and developer tooling. For AI‑specific tools, please see the companion repositories.
1. [vaibhavgawali/gemini-cli](https://hub.docker.com/repository/docker/vaibhavgawali/gemini-cli) → Gemini CLI container for AI workflows
2. [vaibhavgawali/fabric-cli](https://hub.docker.com/repository/docker/vaibhavgawali/fabric-cli) → Fabric CLI container for AI‑powered automation

These AI agents need the required tools from this image.

### 🔑 Key Features
1. .NET 10 SDK
2. Node.js 22.x with npm preinstalled
3. Python 3.x with pip, setuptools, wheel
4. OpenJDK 21 for Java development
5. Secure non‑root user (appuser) for safer builds
6. Clean image following Docker best practices

### 🚀 Quick Usage Examples
Pull the Image
```bash
docker pull vaibhavgawali/dotnet-node-python-openjdk:latest
```
Run Interactive Container
```bash
docker run -it --rm vaibhavgawali/dotnet-node-python-openjdk bash
```
Mount Local Workspace
```bash
docker run -it --rm -v $(pwd):/workspace vaibhavgawali/dotnet-node-python-openjdk bash
```

### 🔧 Verify Installed Runtimes
Inside the container, check versions:

```bash
dotnet --version
node --version
npm --version
python3 --version
java -version
```

### 🛠️ Example Workflows
Build a .NET MAUI Project
```bash
dotnet workload install maui
dotnet new maui -n MyMauiApp
dotnet build MyMauiApp
```

Run a Node.js App
```bash
mkdir node-app && cd node-app
npm init -y
echo "console.log('Hello from Node.js!')" > index.js
node index.js
```

Use Python for Scripting
```bash
echo "print('Hello from Python!')" > script.py
python3 script.py
```

Compile a Java Program
```bash
echo "public class Hello { public static void main(String[] args) { System.out.println(\"Hello from Java!\"); }}" > Hello.java
javac Hello.java
java Hello
```

### 📚 References
1. [.NET Documentation](https://learn.microsoft.com/dotnet/)
2. [Node.js Documentation](https://nodejs.org/en/docs/)
3. [Python Documentation](https://docs.python.org/3/)
4. [OpenJDK Documentation](https://openjdk.org/)
5. [Ubuntu Base Image](https://hub.docker.com/_/ubuntu)
6. [Docker images docker file in GitHub](https://github.com/vaibhav-gawali/dotnet-node-python-openjdk-tools-docker/tree/main)