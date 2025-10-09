```markdown
# 🧑‍💻 Week 3 Lab: Setting Up SonarQube for Static Code Analysis

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Install and set up SonarQube (or SonarCloud)
- Create a SonarQube project and run a static analysis scan on a sample project
- Analyze and interpret the results of a SonarQube report
- Reflect on how automated static analysis complements manual code reviews

---

## 📋 What You'll Need

- SonarQube installed locally **or** SonarCloud (free-tier) set up
- SonarLint extension installed in VS Code (optional)
- The `Calculator.html` file (download or clone the repository)

---

## 🧪 What You'll Do

### 1. Install SonarQube Locally or Set Up SonarCloud

#### **Option 1: Set Up SonarQube Locally**

- Download and unzip SonarQube from the [official site](https://www.sonarqube.org/downloads/)
- Follow the [SonarQube installation guide](https://docs.sonarqube.org/latest/setup/install-server/) for your operating system
- Once installed, open your browser and go to **http://localhost:9000** to access the SonarQube dashboard

**Default login credentials:**
- **Username:** `admin`
- **Password:** `admin`

#### **Option 2: Set Up SonarCloud**

- Go to [SonarCloud](https://sonarcloud.io/) and create an account if you don't have one
- Link your GitHub repository to SonarCloud (if you don't have one, create a test repository)
- Once linked, create a new project in SonarCloud. SonarCloud will guide you through setting up the SonarScanner to analyze your code

---

### 2. Set Up SonarQube for the Calculator Project

#### **Create the Project**

- Clone or download the `Calculator.html` file. This file is your JavaScript Calculator that you'll be analyzing

#### **Configure SonarQube for analysis**

- Create a `sonar-project.properties` file in the project folder and add the following configuration:

```properties
sonar.projectKey=calculator-js-project
sonar.projectName=Calculator JS Project
sonar.projectVersion=1.0
sonar.sources=.
sonar.language=js
sonar.sourceEncoding=UTF-8
```

> This tells SonarQube to analyze the JavaScript code embedded in the `Calculator.html` file.

---

### 3. Run the SonarQube Analysis

- Install SonarScanner by following the [SonarScanner installation guide](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)
- Open your terminal/command prompt and navigate to the folder where the `Calculator.html` file is located
- Run the following command to start the analysis:

```bash
sonar-scanner
```

> This will send your project's code to SonarQube for inspection.

---

### 4. Review the Results in SonarQube

- After the analysis completes, open your browser and go to your SonarQube dashboard (**http://localhost:9000** for local, or your SonarCloud project URL)
- Find the **Calculator Project** and click on it to see the analysis results

You should see the following insights:

- **Code Smells**: Suggestions to improve code quality
- **Bugs**: Functional errors in the code
- **Vulnerabilities**: Potential security risks
- **Test Coverage**: If tests exist, SonarQube will show coverage details

---

### 5. Analyze and Reflect on the Results

#### **Analyze the Report**

Review the SonarQube report and identify:

- Are there any code smells or bugs detected?
- What does SonarQube suggest to improve the code (e.g., refactorings, security fixes)?

#### **Personal reflection on the Process**

- How did SonarQube help you find issues that might have been missed during a manual code review?
- What did you learn from the SonarQube analysis?
- Do you agree with SonarQube's suggestions? Why or why not?

---

## 📝 What You Need to Practice

- **SonarQube Setup**: Submit a screenshot of your SonarQube dashboard showing the analysis of your **Calculator JS Project**
- **SonarQube Report**: Submit a summary of the issues detected by SonarQube, including:
  - At least **3 issues** detected (e.g., bugs, code smells, security vulnerabilities)
  - **Reflection** on SonarQube's findings: Were there any issues SonarQube found that you missed during the manual review?
- **Reflection**: Submit a brief reflection on your experience:
  - What did you find useful about using SonarQube?
  - How does SonarQube help with static testing compared to manual review?

---

## 🧑‍💻 Further Learning

To get deeper into SonarQube:

- Explore **SonarQube Quality Gates** (to ensure code quality before merging)
- Learn about **custom rules and configuration** in SonarQube to tailor it to your project
- Integrate SonarQube with **CI/CD pipelines** for automated analysis during every code push

### 🔗 Additional Resources

- [SonarQube Documentation](https://docs.sonarqube.org/)
- [SonarScanner Documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)
- [SonarCloud Documentation](https://docs.sonarcloud.io/)
- [SonarQube Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/)
```
