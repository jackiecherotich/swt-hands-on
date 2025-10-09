```markdown
# 📝 FAQ for Week 3 Lab: Setting Up SonarQube for Static Code Analysis

## 🎯 General Questions

### 1. What is SonarQube, and why are we using it?

SonarQube is a static code analysis tool that helps detect issues in your code, such as bugs, vulnerabilities, and code smells. It is commonly used in the software development industry to maintain and improve code quality by automatically finding potential problems in codebases. In this lab, you’ll set up SonarQube (or SonarCloud) to analyze a simple JavaScript project and get hands-on experience with automated static code analysis.

### 2. Can I use SonarCloud instead of SonarQube?

Yes! **SonarCloud** is the cloud-based version of SonarQube, and it’s much easier to set up since there’s no need to install anything on your computer. SonarCloud integrates directly with GitHub repositories and doesn’t require Java or other dependencies, making it an ideal option for a quick and easy setup.

If you want to avoid installation hassles and prefer a cloud-based solution, **SonarCloud is the recommended choice**.

### 3. Can SonarQube be used with JavaScript?

Yes! SonarQube supports JavaScript projects via the **SonarJS plugin**, which specifically analyzes JavaScript and TypeScript code. It will detect issues like:

- **Bugs** (e.g., runtime errors)  
- **Code smells** (e.g., inefficient or hard-to-maintain code)  
- **Security vulnerabilities** (e.g., risky code practices like `eval()`)

Even though SonarQube is often used with Java, it works perfectly with JavaScript and is commonly used to analyze JavaScript, TypeScript, and many other languages.

### 4. Can I use SonarLint with VS Code for this lab?

Yes, you can use **SonarLint** for real-time static analysis directly within VS Code! SonarLint provides inline feedback while you write code and can sync with SonarQube or SonarCloud to apply the same rules as the full SonarQube analysis. It's an easy and seamless way to get instant feedback on your JavaScript code.

#### Steps to Use SonarLint in VS Code:

1. **Install SonarLint**: Go to the VS Code marketplace and install the [SonarLint extension](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode).
2. **Link to SonarQube/SonarCloud (Optional)**: In VS Code settings, link SonarLint to your SonarQube or SonarCloud account to use the same set of rules from the full SonarQube analysis.
3. **Analyze Your Code**: As you write your JavaScript code, SonarLint will automatically highlight issues directly in the editor, such as bugs, code smells, and security vulnerabilities.

> **Note**: SonarLint works locally and provides feedback while coding, but it **doesn’t replace the full SonarQube analysis**. It’s great for immediate feedback but doesn’t provide the detailed project-wide reports SonarQube does.

---

## 💻 Installation & Setup

### 5. What do I need to install SonarQube locally?

To install SonarQube locally, you’ll need:

- **SonarQube**: Download from the [official site](https://www.sonarsource.com/products/sonarqube/).
- **Java JDK 11 or later**: SonarQube requires Java to run. If you don’t already have Java 11+, download it from [Adoptium](https://adoptium.net/) or [Oracle](https://www.oracle.com/java/technologies/downloads/).
- **A supported database**: SonarQube uses an embedded **H2 database** by default (perfect for labs), but you can configure it to use PostgreSQL or another database if needed.

Once everything is installed and running, access SonarQube at:  
👉 [http://localhost:9000](http://localhost:9000)

> 💡 **Optional**: If you want to avoid installing Java and SonarQube locally, **SonarCloud is an easier cloud-based alternative**.

### 6. How do I set up SonarCloud?

To use SonarCloud:

1. Go to [SonarCloud](https://sonarcloud.io/) and create an account.
2. Link your **GitHub repository** to SonarCloud (if you don’t have one, create a simple public repo on GitHub).
3. Follow the on-screen setup instructions to integrate your repo and run the analysis.

With SonarCloud, you don’t need to install Java or run SonarQube locally—it integrates directly with GitHub and handles everything in the cloud.

### 7. I can't access the SonarQube dashboard at `http://localhost:9000`. What should I do?

If you're having trouble accessing SonarQube locally, try these steps:

- ✅ **Make sure SonarQube is running**: Check the terminal where you started SonarQube for any startup errors.
- ✅ **Check your Java version**: Run `java -version`—you need **Java 11 or later**.
- ✅ **Firewall settings**: Ensure your firewall or antivirus isn’t blocking port `9000`.
- ✅ **Check SonarQube logs**: Look in the `logs/` directory inside your SonarQube installation folder for error details.

---

## 🔧 SonarQube Configuration

### 8. Where should I place the `sonar-project.properties` file?

Place the `sonar-project.properties` file in the **root directory** of your project (the same folder as `index.js`, `package.json`, etc.). This file tells SonarQube how to analyze your code.

#### Example configuration:
```properties
sonar.projectKey=my-js-project
sonar.projectName=My JavaScript Project
sonar.projectVersion=1.0
sonar.sources=.
sonar.language=js
sonar.sourceEncoding=UTF-8
```

### 9. What does `sonar.sources=.` mean in the `sonar-project.properties` file?

The line `sonar.sources=.` tells SonarQube to analyze **all files in the current directory** (`.`).  
If your JavaScript code lives in a subfolder like `src/`, change it to:
```properties
sonar.sources=src
```

---

## 🛠️ Running the Analysis

### 10. What is SonarScanner, and why do I need it?

**SonarScanner** is the command-line tool that sends your code to SonarQube (or SonarCloud) for analysis. After configuring your project, you run `sonar-scanner` to trigger the static analysis.

You can install SonarScanner by following the [SonarScanner installation guide](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/).

### 11. I ran `sonar-scanner` but nothing happened. What should I do?

If `sonar-scanner` isn’t working:

- 🔍 **Ensure SonarScanner is installed**: Run `sonar-scanner -v` to verify it’s accessible.
- 🔍 **Check error messages**: Look closely at terminal output for clues (e.g., missing config, network issues).
- 🔍 **Verify `sonar-project.properties`**: Confirm the file exists in the correct directory and contains valid settings (e.g., correct `sonar.host.url` for SonarCloud).

---

## 🔍 Understanding SonarQube Results

### 12. What are "code smells"?

**Code smells** refer to patterns in your code that might indicate potential problems. These issues may not be bugs, but they could make the code harder to maintain. Common examples include:

- **Long functions**: Functions that do too much and are hard to understand.
- **Duplicated code**: The same logic repeated in multiple places.
- **Inconsistent naming**: Variables or functions with unclear or misleading names.

SonarQube highlights these to improve **code maintainability**.

### 13. What are "vulnerabilities"?

A **vulnerability** is a security flaw that could expose your application to risks (e.g., injection attacks, data leaks). SonarQube detects these based on known security anti-patterns and coding best practices.

### 14. What does SonarQube mean by "bugs"?

**Bugs** are actual errors in your code that cause incorrect behavior or crashes (e.g., null pointer dereferences, infinite loops). SonarQube identifies these to prevent runtime failures.

### 15. What should I do if SonarQube flags an issue I don’t agree with?

If SonarQube flags an issue you believe is not relevant:

- ✅ **Review carefully first**: Many rules are based on industry best practices—double-check before dismissing.
- 🚫 **Ignore the rule**: You can suppress specific rules globally or per file (use sparingly).
- 🏷️ **Mark as "Won’t Fix"**: In the SonarQube UI, you can mark issues as “Won’t Fix” with a comment explaining why.

> 💡 **Best practice**: Treat SonarQube suggestions as learning opportunities—even if you disagree, understand *why* it was flagged.

---

## 🤔 Reflection & Troubleshooting

### 16. What should I include in my reflection for the lab?

In your reflection, consider:

- **How useful was SonarQube?**  
  Did it catch bugs, smells, or vulnerabilities you missed during manual review?
  
- **What did you learn?**  
  What new insights did you gain about static analysis, code quality, or secure coding?

- **Challenges faced:**  
  Were there setup, configuration, or interpretation issues? How did you resolve them?

---

## 🗂️ Other Helpful Links

- [SonarQube Documentation](https://docs.sonarsource.com/sonarqube/)
- [SonarScanner Documentation](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/)
- [SonarCloud Documentation](https://docs.sonarcloud.io/)
- [SonarQube Quality Gates](https://docs.sonarsource.com/sonarqube/latest/user-guide/quality-gates/)
```
