# Module 3 — Project Setup & Security Foundations

> *"Most security failures don't happen in complex logic —  
they happen in careless setup."*

---

## 🎯 Module Goal

Set up a **clean, professional, security-aware backend project**  
that feels like real-world engineering — not tutorial chaos.

By the end of this module, you will:
- Understand **why structure matters for security**
- Know **what each dependency is responsible for**
- Be able to spot **dangerous setup mistakes** in real projects
- Start coding with **clarity, not confusion**

This module is **self-paced**. Take your time. Read, reflect, then implement.

---

## 🧠 Why This Module Matters

Many developers rush into:
- Writing routes
- Copy-pasting auth logic
- Following random folder structures

But attackers don't care about your routes —  
they exploit **misconfigurations**.

Examples:
- `.env` pushed to GitHub
- Secrets hardcoded in files
- Confusing folder layouts
- Overloaded files with mixed responsibility

👉 **Security starts before the first line of business logic.**

---

## 🛠 Topics Covered

### 1️⃣ Express Server Structure (Clean & Predictable)

You will learn:
- Why `server.js` should stay **thin**
- Why routes, models, and logic must be separated
- How clean structure improves:
  - Security audits
  - Debugging
  - Team collaboration

> Think like this:  
> *"If someone new joins my team, can they understand this in 5 minutes?"*

---

### 2️⃣ Environment Variables (`.env`)

You will understand:
- What environment variables are
- Why **secrets must NEVER live in code**
- How production systems load secrets differently

Examples of secrets:
- Database connection strings
- JWT secret keys
- API keys
- Admin credentials

📌 **Golden rule**  
> If it's secret, it never belongs in GitHub.

---

### 3️⃣ Why Secrets Must Never Go to GitHub

Real-world consequences:
- GitHub scanners automatically detect exposed secrets
- Bots scrape public repos within minutes
- One leaked secret can:
  - Expose your entire database
  - Allow fake token generation
  - Compromise user accounts

You'll learn:
- Why `.gitignore` exists
- Why leaked secrets must be rotated immediately
- Why "private repo" ≠ safe

---

### 4️⃣ Dependency Responsibility (Critical Thinking)

Instead of blindly installing packages, you will learn **why each exists**:

| Dependency         | Responsibility                        |
| ------------------ | ------------------------------------- |
| express            | HTTP server & routing                 |
| mongoose           | Database schema & queries             |
| bcrypt             | Password hashing + salt + cost factor |
| jsonwebtoken       | Token creation & verification         |
| dotenv             | Secure environment configuration      |
| cors               | Controlled cross-origin access        |
| express-rate-limit | Brute-force protection                |


📌 **Key mindset**  
> Every dependency increases power — and attack surface.

---

## 🗂 Folder Structure (Professional Standard)

You will use this structure throughout the course:

<img width="491" height="237" alt="image" src="https://github.com/user-attachments/assets/fcb3becf-cfb5-4ded-bdca-7a1ce1966f1e" />


### Why This Structure Works

- Clear separation of concerns
- Easier security audits
- Easy to scale
- Matches real production codebases

> If your project structure is messy,  
> your security thinking usually is too.

---

## 🔑 Key Concepts (Read Carefully)

### 🔐 Configuration vs Code
- **Code** = logic that runs
- **Configuration** = values that change per environment

Mixing them is dangerous.

---

### 🔥 Why Production Security Starts at Setup
- Weak setup → weak security
- Secure logic on top of insecure config is useless
- Hackers often exploit:
  - Open ports
  - Default credentials
  - Exposed environment variables

---

### ⚠️ Misconfigured Projects as Attack Vectors

Common mistakes you'll learn to avoid:
- Hardcoding JWT secrets
- Committing `.env`
- Using same secret in dev & prod
- Leaving unused dependencies installed

---

## 🧪 Self-Paced Reflection (Important)

Before moving on, ask yourself:

- Can I explain **why each folder exists**?
- Do I know **which file contains secrets**?
- Can I identify **what NOT to commit to GitHub**?
- Do I understand **what each dependency is responsible for**?

If yes → you're ready.

---

## ✅ Module Outcome

By completing this module, you now:

✔ Have a clean, professional backend structure  
✔ Understand why setup decisions impact security  
✔ Avoid common beginner & startup security mistakes  
✔ Are mentally prepared to implement authentication correctly  

---

## ⏭ What's Next

In the next module, you will move from **setup to substance**:

> 🔐 **Module 4 — Password Security: Hashing, Salting & Cost Factor**

This is where you'll:
- Store passwords incorrectly (on purpose)
- See how attackers exploit it
- Fix it the **right way**

👉 Proceed only when you feel confident with this foundation.
