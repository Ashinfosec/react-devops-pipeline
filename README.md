# DevOps Pipeline Learning


I built this project to learn modern DevOps practices hands-on. 

##  What I Built

I took a React web application I deeveloped and built a complete production-ready DevOps pipeline around it.

```
My Local Setup → Azure DevOps → Docker → Production Ready
     ↓              ↓           ↓            ↓
  React App    →  Pipeline  →  Container → Quality Checks
```

##  Tech Stack I Used

- **Frontend**: React + Vite (because it's fast and modern)
- **CI/CD**: Azure DevOps with my own self-hosted agent
- **Containerization**: Docker (learned multi-stage builds!)
- **Security**: Trivy for container scanning
- **Code Quality**: SonarQube (this was eye-opening)
- **Infrastructure**: Windows self-hosted agent running locally

##  The Pipeline I Built

### Stage 1: Build & Test
This is where I start with my React code and make sure everything works:
- Install Node.js and dependencies
- Run `npm audit` to catch vulnerable packages
- Build the app with Vite
- Save the build artifacts for later stages

### Stage 2: Docker & Security Scanning
Here I package everything into a container and scan it for vulnerabilities:
- Build a Docker image with my React app
- Run Trivy security scanner on the container
- Tag images properly for version tracking
- Clean up afterwards (learned this the hard way when my disk filled up)

### Stage 3: Code Quality Analysis
This stage humbled me the most:
- SonarQube analyzes my code for bugs, security issues, and code smells
- Generates coverage reports (currently 0% - I know, I need tests!)
- Creates security hotspot reports
- Sets up quality gates for future improvements


##  Security Features I Implemented

I wanted to understand security scanning at multiple levels:

- **Container Security**: Trivy scans my Docker images for known vulnerabilities
- **Code Security**: SonarQube finds potential security issues in my JavaScript
- **Dependency Security**: npm audit catches vulnerable packages
- **Secret Management**: Used Azure DevOps Variable Groups (no more hardcoded tokens!)


### Technical Skills
- **Azure DevOps**: Setting up agents, managing variable groups, creating pipelines
- **Docker**: Multi-stage builds, optimization, security considerations
- **Security Tools**: Trivy for containers, SonarQube for code analysis
- **Pipeline as Code**: Everything defined in YAML and version controlled




##  How to Run This Yourself

If you want to recreate this learning experience:

### Prerequisites
- Azure DevOps account (free tier works)
- Docker installed locally
- Node.js 18.x
- A Windows machine for the self-hosted agent (or adapt for Linux)

### Setup Steps
1. **Clone a react repo/ create your own project** and look at the `azure-pipelines.yml` I provided
2. **Set up SonarQube** locally: `docker run -d -p 9000:9000 sonarqube:latest`
3. **Configure your Azure DevOps agent** (running my locally)
4. **Create a Variable Group** STORE YOUR PAT TOKEN OR OTHER SECRETS TO AVOID HARDCODED 
5. **Run the pipeline** and watch it 
