# Azerbaijani Language Support Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add full Azerbaijani ("az") translation support to the theme by creating `locales/az.json` and verifying it with `gscan`.

**Architecture:** A new locale file `locales/az.json` will be added to the project, mirroring the keys from `locales/en.json` and adding necessary localizations from `locales/tr.json` to support newer visual and functional features in Azerbaijani.

**Tech Stack:** JSON, Ghost theme i18n, gscan

---

### Task 1: Create Azerbaijani Locale File

**Files:**
- Create: `locales/az.json`

- [ ] **Step 1: Write the minimal initial JSON file**

Create the file `locales/az.json` with the following content:

```json
{
    " (Page %)": " (Səhifə %)",
    " and ": " və ",
    "% issues": "% say",
    "% min": "% dəqiqə",
    "% min read": "% dəqiqəlik oxu",
    "0 issues": "0 say",
    "1 issue": "1 say",
    "1 min": "1 dəqiqə",
    "1 min read": "1 dəqiqəlik oxu",
    "A collection of 0 issues": "0 saydan ibarət kolleksiya",
    "A collection of 0 posts": "0 məqalədən ibarət kolleksiya",
    "A collection of 1 issue": "1 saydan ibarət kolleksiya",
    "A collection of 1 post": "1 məqalədən ibarət kolleksiya",
    "A collection of {numberOfIssues} issues": "{numberOfIssues} saydan ibarət kolleksiya",
    "A collection of {numberOfPosts} posts": "{numberOfPosts} məqalədən ibarət kolleksiya",
    "About": "Haqqında",
    "Access site": "Sayta daxil ol",
    "Account": "Hesab",
    "Additional issues will be published soon.": "Əlavə saylar tezliklə dərc olunacaq.",
    "All episodes": "Bütün bölümlər",
    "All episodes →": "Bütün bölümlər →",
    "Already have an account?": "Artıq hesabınız var?",
    "Archive": "Arxiv",
    "Browse all issues": "Bütün saylara göz gəzdir",
    "Browse archive": "Arxivə göz gəzdir",
    "By {authors}": "{authors} tərəfindən",
    "By {primaryAuthor}": "{primaryAuthor} tərəfindən",
    "Close (Esc)": "Bağla (Esc)",
    "Comments": "Şərhlər",
    "Copy and share": "Kopyala və paylaş",
    "Don't miss out on the latest issues. Sign up now to get access to the library of members-only issues.": "Ən son sayları qaçırmayın. Yalnız üzvlər üçün nəzərdə tutulmuş saylar kitabxanasına daxil olmaq üçün indi qeydiyyatdan keçin.",
    "Email sent": "E-poçt göndərildi",
    "Enter your email": "E-poçtunuzu daxil edin",
    "Featured": "Seçilmişlər",
    "Go to the front page →": "Ana səhifəyə keç →",
    "Latest": "Ən son",
    "Latest episodes": "Son bölümlər",
    "Latest issue": "Son say",
    "Learn more": "Daha ətraflı",
    "Link copied!": "Keçid kopyalandı!",
    "Listen on": "Dinləyin",
    "Load more issues": "Daha çox say yüklə",
    "Load more": "Daha çox yüklə",
    "Login": "Daxil ol",
    "Member discussion": "Üzv müzakirəsi",
    "Member discussion:": "Üzv müzakirəsi:",
    "Members": "Üzvlər",
    "Members only": "Yalnız üzvlər üçün",
    "Menu": "Menyu",
    "More": "Daha çox",
    "More issues": "Daha çox say",
    "More links": "Daha çox keçid",
    "Newer Posts": "Daha yeni məqalələr",
    "Next": "Növbəti",
    "Next (arrow right)": "Növbəti (sağ ox)",
    "Next issue": "Növbəti say",
    "Next post": "Növbəti məqalə",
    "Next →": "Növbəti →",
    "Older Posts": "Daha köhnə məqalələr",
    "Page {page} of {totalPages}": "Səhifə {page} / {totalPages}",
    "Paid": "Ödənişli",
    "Paid-members only": "Yalnız ödənişli üzvlər üçün",
    "Password": "Şifrə",
    "Powered by Ghost": "Ghost ilə hazırlanmışdır",
    "Powered by {ghostlink}": "{ghostlink} tərəfindən dəstəklənir",
    "Previous": "Əvvəlki",
    "Previous (arrow left)": "Əvvəlki (sol ox)",
    "Previous issue": "Əvvəlki say",
    "Previous post": "Əvvəlki məqalə",
    "Published by:": "Dərc edən:",
    "RSS": "RSS",
    "Read latest issue": "Son sayı oxu",
    "Read more": "Daha çox oxu",
    "Read next": "Növbətini oxu",
    "Recent posts": "Son məqalələr",
    "Recommendations": "Tövsiyələr",
    "Search posts, tags and authors": "Məqalələrdə, etiketlərdə və müəlliflərdə axtar",
    "Search this site": "Saytda axtar",
    "See all": "Hamısına bax",
    "Share": "Paylaş",
    "Show more": "Daha çox göstər",
    "Sign in": "Daxil ol",
    "Sign in.": "Daxil olun.",
    "Sign up now to get access to the library of members-only issues.": "Yalnız üzvlər üçün nəzərdə tutulmuş saylar kitabxanasına daxil olmaq üçün indi qeydiyyatdan keçin.",
    "Stay tuned": "Bizi izləməyə davam edin",
    "Subscribe": "Abunə ol",
    "Subscribe now": "İndi abunə ol",
    "Subscribe to {sitetitle}": "{sitetitle} saytına abunə ol",
    "Theme errors": "Tema xətaları",
    "This page is for paying subscribers only": "Bu səhifə yalnız ödənişli abunəçilər üçündür",
    "This page is for subscribers on the {tiers} only": "Bu səhifə yalnız {tiers} abunəçiləri üçündür",
    "This page is for subscribers only": "Bu səhifə yalnız abunəçilər üçündür",
    "This post is for paying subscribers only": "Bu məqalə yalnız ödənişli abunəçilər üçündür",
    "This post is for subscribers on the {tiers} only": "Bu məqalə yalnız {tiers} abunəçiləri üçündür",
    "This post is for subscribers only": "Bu məqalə yalnız abunəçilər üçündür",
    "This site is private.": "Bu sayt özəldir.",
    "Toggle fullscreen": "Tam ekran",
    "Toggle menu": "Menyu",
    "Topic": "Mövzu",
    "Topics": "Mövzular",
    "Upgrade": "Yüksəlt",
    "Upgrade now": "İndi yüksəlt",
    "Upgrade to a paid account to get full access.": "Tam giriş əldə etmək üçün ödənişli hesaba yüksəldin.",
    "Upgrade your account": "Hesabınızı yüksəldin",
    "View all →": "Hamısına bax →",
    "View project": "Layihəyə bax",
    "Website": "Vebsayt",
    "You might also like...": "Bunlar da xoşunuza gələ bilər...",
    "Zoom in/out": "Yaxınlaşdır/Uzaqlaşdır",
    "comment": "şərh",
    "comments": "şərh",
    "in {primaryTag}": "{primaryTag} daxilində",
    "jamie@example.com": "nümunə@e-poçt.com",
    "← Previous": "← Əvvəlki"
}
```

- [ ] **Step 2: Save the file**

Confirm that `locales/az.json` is correctly written on disk.

---

### Task 2: Validate Locale File and Theme

**Files:**
- Test: `locales/az.json`

- [ ] **Step 1: Check JSON Syntax Validity**

Run a check to ensure the JSON structure is perfectly valid.
Run: `node -e "JSON.parse(require('fs').readFileSync('locales/az.json'))"`
Expected: No errors (exit code 0).

- [ ] **Step 2: Run Theme Validation**

Run the theme validator `gscan` to check that the newly added locale and all theme components compile and validate cleanly.
Run: `npm run test` (which triggers `gscan .`)
Expected: Passes successfully with no strict compatibility issues or errors.
