# ✅ RECRUITER PROFILE PLAN (Production-Ready)

# 1️⃣ Recruiter Profile Information Structure

A recruiter profile should have **4 main sections**:
* **A. Personal Recruiter Info**
* **B. Company Info**
* **C. Verification Info**
* **D. Hiring Preferences**

# 2️⃣ A. Personal Recruiter Info (Required)
These fields prove the recruiter is a real professional person.

### Required Fields

* **Full Name** *(required)*
* **Profile Photo** *(required)*
* **Designation / Job Title** *(required)*

  * Example: HR Manager, Talent Acquisition Specialist, Recruiter
* **Official Work Email** *(required)*
* **Phone Number** *(required)*
* **Location (City, Country)** *(required)*
* **Short Bio / About Recruiter** *(required)*
* **Years of Recruitment Experience** *(optional but recommended)*

### Why needed

This builds **basic personal trust**.


# 3️⃣ B. Company Information (Required)

This is the **most important section** for authenticity.

### Required Fields

* **Company Name** *(required)*
* **Company Logo** *(required)*
* **Company Website** *(required)*
* **Company Industry** *(required)*
* **Company Size** *(required)*
* **Company Location / Headquarters** *(required)*
* **Company Description** *(required)*

### Strongly Recommended Fields

* **Founded Year**
* **Office Address**
* **LinkedIn Company Page**
* **Company Registration Number / Trade License**
* **Business License / Registration Document Upload**

### Why needed

Without company info, the recruiter can look **fake**.

# 4️⃣ C. Verification Information (Required)

This section controls trust and posting permission.

### Verification Fields

* **Email Verified** ✅ *(required before job posting)*
* **Phone Verified** *(optional for now, can add later)*
* **Company Domain Match** *(recommended)*

  * Example: email = `hr@abc.com`
  * website = `abc.com`
* **Admin Verification Status**

  * `pending`
  * `verified`
  * `rejected`

### Best rule

For now, you can start with:

* **Email verification required**
* **Admin verification optional but recommended**

# 5️⃣ D. Hiring Preferences (Required for Job Posting)

These fields make the recruiter ready to post relevant jobs.
Job Title
Category
Job Type
Work Mode
Location
Salary
Experience
Skills
Description
Deadline
Vacancy

  * Full-time / Part-time / Internship / Contract / Remote



# 6️⃣ Email Verification Rule (MUST HAVE)

For your app, this should be **mandatory**.

## Rule:

* Recruiter signs up with email/password
* Firebase sends verification email
* Recruiter must verify email before posting jobs

### Best logic

* **If email not verified** → cannot post job ❌
* **If email verified** → continue to profile completion check ✅

### UI message

> “Please verify your email before posting a job.”

This is simple, professional, and free with Firebase.

---

# 7️⃣ Profile Completion Rule for Job Posting (Best for Your Platform)

You already want a **profile completion rule**, which is excellent.

## Recommended Rule:

* **Profile completion must be at least 70%**
* **Email must be verified**
* Then only the recruiter can **post jobs**

### Final Posting Rule:

A recruiter can post a job **ONLY IF**:

* **Email is verified** ✅
* **Profile completion ≥ 70%** ✅

Otherwise:

* **Posting blocked** ❌

---

# 8️⃣ Best Profile Completion Percentage Logic (Production-Ready)

Use **weighted sections** instead of counting random fields.

---

## Section Weights

### **A. Personal Info = 30%**

* Full Name → 5%
* Profile Photo → 5%
* Designation → 5%
* Official Work Email → 5%
* Phone Number → 5%
* Bio → 5%

---

### **B. Company Info = 40%**

* Company Name → 5%
* Company Logo → 5%
* Company Website → 5%
* Company Industry → 5%
* Company Size → 5%
* Company Location → 5%
* Company Description → 10%

---

### **C. Verification = 20%**

* Email Verified → 20%

> This makes email verification very important.

---

### **D. Hiring Preferences = 10%**

* Hiring Roles / Categories → 4%
* Departments Hiring For → 3%
* Employment Types → 3%

---

# ✅ Total = 100%

---

# 9️⃣ Job Posting Permission Logic (Recommended)

## Allow job posting only if:

```text
emailVerified === true
AND
profileCompletion >= 70
```

### Optional advanced rule:

```text
if profileCompletion >= 70 and emailVerified === true:
    allow job post
else:
    block job post
```

---

# 🔟 Best Posting Restriction Messages

### If email not verified:

> “Please verify your email to unlock job posting.”

### If profile below 70%:

> “Complete at least 70% of your recruiter profile to post jobs.”

### If both missing:

> “Verify your email and complete at least 70% of your profile to post jobs.”

---

# 1️⃣1️⃣ Best Recruiter Verification Levels (Recommended)

To make your platform professional, create **3 trust levels**:

---

## **Level 1 — Basic Recruiter**

* Registered account
* Email not verified yet
* Can edit profile
* Cannot post jobs

---

## **Level 2 — Active Recruiter**

* Email verified
* Profile completion ≥ 70%
* Can post jobs

---

## **Level 3 — Verified Recruiter**

* Email verified
* Profile completion ≥ 70%
* Admin approved
* Optional business documents uploaded
* Show **Verified Badge**

---

# 1️⃣2️⃣ Recommended Admin Flow

Admin should be able to:

* View recruiter profile
* See email verification status
* See profile completion %
* See company info
* Approve / reject recruiter
* Add verified badge
* Suspend fake recruiters

### Admin statuses:

* `pending`
* `approved`
* `rejected`
* `suspended`

---

# 1️⃣3️⃣ Best Database Fields for Recruiter (Simple Structure)

Here is the **recommended data structure** for your recruiter:

```javascript id="7brm4t"
{
  role: "recruiter",
  fullName: "",
  profilePhoto: "",
  designation: "",
  email: "",
  emailVerified: false,
  phone: "",
  location: "",
  bio: "",

  companyName: "",
  companyLogo: "",
  companyWebsite: "",
  companyIndustry: "",
  companySize: "",
  companyLocation: "",
  companyDescription: "",

  hiringRoles: [],
  departments: [],
  employmentTypes: [],

  profileCompletion: 0,
  canPostJob: false,

  adminVerificationStatus: "pending", // pending | approved | rejected | suspended
  isVerifiedRecruiter: false,

  createdAt: "",
  updatedAt: ""
}
```

---

# 1️⃣4️⃣ Best System Workflow (Very Important)

## Recruiter onboarding flow:

### Step 1: Sign Up

* Recruiter creates account with email/password

### Step 2: Email Verification

* Firebase sends verification email

### Step 3: Login

* Recruiter logs in

### Step 4: Complete Profile

* Fill personal info
* Fill company info
* Fill hiring preferences

### Step 5: System calculates profile completion

* Based on weighted fields

### Step 6: Posting rule check

If:

* Email verified = true
* Profile completion ≥ 70

Then:

* `canPostJob = true`

Else:

* `canPostJob = false`

### Step 7: Job Post Access

* If `canPostJob === true` → show “Post Job” button enabled
* Else → disable button and show warning

---

# 1️⃣5️⃣ Best UI Sections for Recruiter Dashboard

Show these cards on recruiter dashboard:

* **Profile Completion %**
* **Email Verification Status**
* **Can Post Job Status**
* **Missing Required Fields**
* **Company Verification Status**
* **Complete Profile CTA Button**

### Example:

* Profile Completion: **62%**
* Email Verified: **No**
* Can Post Job: **No**
* Missing:

  * Company Logo
  * Company Description
  * Hiring Roles
  * Email Verification

This makes the system very user-friendly.

---

# 1️⃣6️⃣ Best Final Rule for Your App (Recommended)

## Final production-ready rule:

### Recruiter can post a job only when:

* **Email is verified**
* **Profile completion is 70% or more**

### Optional future upgrade:

* Admin approved recruiter = gets verified badge

---

# ✅ Final Recommended Version (Simple + Strong)

## Required to post jobs:

* Full name
* Profile photo
* Designation
* Email
* Email verified
* Phone number
* Bio
* Company name
* Company logo
* Company website
* Company industry
* Company size
* Company location
* Company description
* Hiring roles
* Departments
* Employment types
* Profile completion ≥ 70%

---

# ✅ Short Simple Rule

### **Posting Rule**

A recruiter **cannot post jobs** unless:

* **Email is verified**
* **Profile completion is at least 70%**

---

# 🚀 Best Recommendation for Your Project

For your current stage, I strongly recommend this exact version:

### **Phase 1 (Implement now)**

* Email verification via Firebase
* Profile completion %
* 70% required
* Block posting until both conditions pass

### **Phase 2 (Implement later)**

* Admin recruiter verification
* Company document upload
* Verified badge

---

If you want, I can give you next **in one full production-ready answer**:

### **1. Full MongoDB/Mongoose Recruiter Schema**

### **2. Exact profile completion calculation function**

### **3. Backend job posting middleware rule**

### **4. Frontend dashboard logic**

### **5. A single full implementation prompt for your JavaScript app**