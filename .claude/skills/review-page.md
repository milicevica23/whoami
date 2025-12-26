---
name: review-page
description: Review a page for English improvements and critical thinking suggestions on how to improve it
model: opus
---

# Review Page Skill

You are reviewing a page on the user's blog for English improvements and critical thinking suggestions.

## Steps to follow:

1. **Parse the page name from the arguments**: The user will provide a page name like `about`, `blog/some-post`, etc.

2. **Locate the file**:
   - For simple names like `about`, look for `content/about.md` or `content/about/_index.md`
   - For blog posts like `blog/post-name`, look for `content/blog/post-name/index.md`
   - For other content, search in the `content/` directory

3. **Read the file content** using the Read tool.

4. **Provide a comprehensive review** with two main sections:

---

## ENGLISH IMPROVEMENTS

Review the content for:
- Grammar errors (subject-verb agreement, tense consistency, articles, prepositions)
- Spelling and punctuation mistakes
- Awkward phrasing or unclear sentences
- Word choice improvements (more precise, engaging vocabulary)
- Sentence flow and transitions
- Redundancies and wordiness

For each issue, provide:
- The original text
- The suggested correction
- Brief explanation why

---

## CRITICAL THINKING: HOW TO IMPROVE THE PAGE

Analyze the page strategically and provide suggestions for:

1. **Content Structure**: Is the information organized logically? Are there missing sections?

2. **Messaging Clarity**: Is the main message clear? Does it achieve its purpose?

3. **Audience Engagement**: Will readers find this compelling? What could hook them better?

4. **Credibility & Trust**: Are claims supported? Would examples or data strengthen it?

5. **Call to Action**: If applicable, is there a clear next step for readers?

6. **SEO & Discoverability**: Title, headers, keywords - any improvements?

7. **Visual/Formatting**: Would the content benefit from better formatting, lists, or sections?

---

## OUTPUT FORMAT

```
## English Improvements

### Grammar & Spelling
[List corrections in before/after format]

### Style & Clarity
[Suggestions to improve readability]

---

## Critical Thinking: Page Improvement Ideas

### High Priority
[Most impactful changes]

### Medium Priority
[Nice-to-have improvements]

### Low Priority / Future Ideas
[Optional enhancements]

---

## Summary
[1-2 sentence overall assessment and top 3 recommendations]
```

Be constructive and specific. Prioritize actionable feedback that will genuinely improve the page.
