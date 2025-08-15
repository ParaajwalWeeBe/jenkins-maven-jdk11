# Jenkins Maven Build with JDK 11

This repository documents the setup of a Jenkins Freestyle job to build a Maven project using **OpenJDK 11** inside a Dockerized Jenkins environment.

---

## 🛠️ Environment

- **Base Image**: `jenkins/jenkins:lts`
- **OS**: Debian (Bullseye/Bookworm)
- **JDK Installed**: OpenJDK 11
- **Maven**: Configured via Jenkins Global Tool Configuration

---

## ⚙️ Setup Steps

### 1. Install OpenJDK 11 in Jenkins Container

```bash
apt-get update
apt-get install -y openjdk-11-jdk
```

Verify:
```bash
ls /usr/lib/jvm
# java-11-openjdk-arm64
```

---

## ⚙️ Step 2: Configure JDK in Jenkins

1. Navigate to:  
   `Manage Jenkins → Global Tool Configuration → JDK`

2. Add a new JDK entry:
   - **Name**: `JDK_11`
   - ❌ Uncheck **Install automatically**
   - **Tool Home**: `/usr/lib/jvm/java-11-openjdk-arm64`

---

## 🧪 Step 3: Create Maven Freestyle Job

1. Go to:  
   `New Item → Freestyle Project`

2. Configure the job:
   - **Source Code Management**: Git
   - **Build Tool**: Maven
   - **JDK**: `JDK_11`
