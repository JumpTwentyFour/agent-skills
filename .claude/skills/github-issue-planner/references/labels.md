# Labels

- **Security** - Security issue (#e11d48)
- **Performance** - Performance issue (#f59e0b)
- **Stability** - Stability issue (#8b5cf6)
- **Backend** - Backend work with Laravel/PHP (#3b82f6)
- **Frontend** - Frontend work with JavaScript/CSS (#06b6d4)
- **Database** - Work involving the database (#10b981)
- **Code Quality** - Code quality issue (#6366f1)
- **Upgrade** - Dependency upgrade work (#ec4899)
- **Critical** - Critical issue (#dc2626)
- **High** - High urgency issue (#ea580c)
- **Medium** - Medium urgency issue (#f59e0b)
- **Low** - Low urgency issue (#84cc16)

## Label Management Process

**IMPORTANT:** Before applying labels to an issue, ensure the labels exist in the repository.

### 1. Check existing labels

```bash
gh label list
```

### 2. Create missing labels

```bash
gh label create "Security" --color "e11d48" --description "Security issue"
gh label create "Performance" --color "f59e0b" --description "Performance issue"
gh label create "Stability" --color "8b5cf6" --description "Stability issue"
gh label create "Backend" --color "3b82f6" --description "Backend work with Laravel/PHP"
gh label create "Frontend" --color "06b6d4" --description "Frontend work with JavaScript/CSS"
gh label create "Database" --color "10b981" --description "Work involving the database"
gh label create "Code Quality" --color "6366f1" --description "Code quality issue"
gh label create "Upgrade" --color "ec4899" --description "Dependency upgrade work"
gh label create "Critical" --color "dc2626" --description "Critical issue"
gh label create "High" --color "ea580c" --description "High urgency issue"
gh label create "Medium" --color "f59e0b" --description "Medium urgency issue"
gh label create "Low" --color "84cc16" --description "Low urgency issue"
```

### 3. Apply labels to the issue

```bash
gh issue edit <issue-number> --add-label "Security,Backend,Critical"
```

## Label Selection Guide

| Issue Type | Labels to Apply |
|------------|-----------------|
| Security issues | Security + urgency (Critical if P1) + tech area |
| Performance issues | Performance + urgency + tech area |
| Stability issues | Stability + urgency + tech area |
| Code quality issues | Code Quality + tech area |
| Dependency updates | Upgrade + tech area |
