# Basic Concepts
##  How Authentication Really Works

I used to think website security was simple.

Take a password.  
Encrypt it.  
Done.

Then I started asking uncomfortable questions:

- Why do big companies still get hacked?  
- Why does “Login with Google” even exist if passwords are secure?  
- Why do developers talk about **bcrypt**, **JWT**, **OAuth** like they’re magic spells?

This is the story of how I finally connected all the dots — from **hashing** to **authorization** — in a way that *actually* made sense.

---

## 🚪 The First Door: Storing Passwords

Imagine you run a website.  
Users sign up. They trust you with their passwords.

If you store them like this:

username | password
faiz | password123

text

You’ve already failed.

Because databases leak.  
Not *if*. **When.**

So the first lesson is simple:

> **Never store passwords in plain text.**

---

## 🔐 Hashing: Turning Secrets into One-Way Locks

Instead of storing the password, we store a **hash**.

Hashing is like grinding wheat into flour — you can’t turn flour back into wheat.

password123 → e99a18c428cb38d5f260853678922e03

text

The same password always gives the same hash.  
Change one letter, and the hash changes completely.

At first, hashing feels perfect…  
Until you notice the crack.

---

## 🧂 Salting: The Crack You Didn’t See Coming

Two users choose the same password → same hash.  
That’s a problem.

Attackers don’t guess passwords one by one — they use **rainbow tables**, giant lists of password-hash pairs.

To fix that, we **add salt** — random data before hashing:

password123 + X7#@ → hashA
password123 + P9!Q → hashB

text

Same password. Different hash.

> The salt isn’t secret — it breaks predictability.

Rainbow tables? Useless now.  
But attackers still evolve.

---

## 🐢 Why Speed Is the Enemy of Security

Computers are fast — *too fast*.  
They can test **billions** of hashes per second.

So even salted hashes can be brute-forced.

Here’s the twist:  
Security engineers make hashing **slow** *on purpose*.

That’s the **cost factor**.  
It makes guessing expensive.

- For real users → a small delay.  
- For attackers → a nightmare.

---

## 🛡️ bcrypt: When All Three Come Together

That’s where **bcrypt** comes in.

bcrypt:
- Adds salt automatically  
- Uses a cost factor  
- Repeats hashing thousands of times  
- Adapts as computers get faster

A bcrypt hash looks messy:

$2b$12$e9FZbZzH1u1P1b9vYxZs.e...

text

But it’s beautiful inside: version, cost, salt, and hash — all in one string.

Now you store it.  
Forget the password forever.  
Problem solved… or so it seems.

---

## 🛂 Authentication: Proving Who You Are

When a user logs in, the big question is:

> **“Are you really you?”**

The process:
1. Server takes the entered password.  
2. Hashes it using bcrypt.  
3. Compares it to the stored hash.

If they match → identity confirmed.  
No password is ever decrypted — because there’s nothing to decrypt.

Authentication = verifying identity.  
Access is another matter.

---

## 🚦 Authorization: Power Is Not Equal for Everyone

Logging in ≠ having full access.

- A regular user shouldn’t delete accounts.  
- An admin shouldn’t modify financial records casually.

Authorization answers:  
> **“What are you allowed to do?”**

Most security breaches don’t stem from weak passwords — they happen when authorization checks are missing.

---

## 🪪 JWT: The ID Card You Carry After Login

After authentication, the server must *remember* you.

Instead of asking for your password again, it gives you a **JWT** — a digital ID card.

JWT:
- Issued after login  
- Signed by the server  
- Sent with every request  
- Tamper-proof

> **bcrypt opens the door. JWT lets you walk inside.**

JWT doesn’t replace hashing; it builds on it.

---

## 🔑 OAuth: Trusting Someone Else’s Door

“Login with Google” isn’t magic — it’s **delegation**.

You’re saying:

> “Google, confirm who I am.  
> App, trust Google — not my password.”

OAuth exists because:
- Password reuse is risky  
- Users trust identity providers  
- Sharing passwords is never okay

OAuth often uses tokens (sometimes JWTs), but it solves a *social* problem, not a cryptographic one.

---

## 🔄 When Everything Finally Clicks

That’s when it all made sense:

| Concept | Purpose |
|----------|----------|
| Hashing | Protects secrets |
| Salting | Removes predictability |
| Cost factor | Slows attackers |
| bcrypt | Combines all three |
| Authentication | Proves identity |
| Authorization | Controls power |
| JWT | Maintains identity |
| OAuth | Delegates trust |

Each piece exists because the last one wasn’t enough.  
Security evolved by *learning from failure*.

---

## 🧠 Final Thought

Most hacks don’t break math.  
They exploit missing layers.

The biggest mistake developers make:

> “One security tool is enough.”

It never is.

**Security isn’t a feature.**  
It’s a story of careful decisions.
