# AI Assistant Instructions - Development Best Practices

## 🤖 AI ASSISTANT: READ THIS FIRST!

**This file (CLAUDE.md) is your PRIMARY instruction set. It is automatically loaded into your context at the start of EVERY session.**

### How to Ensure These Instructions Are Always Followed:

1. **File Location**: Keep this file as `CLAUDE.md` in the repository root
2. **Claude Desktop/API**: This file is auto-loaded when present
3. **Other AI Tools**: Reference this file first in your prompts
4. **Updates**: Any changes here apply to ALL future sessions

⚠️ **PRIORITY ORDER**:

1. FIRST: Read and follow CLAUDE.md (this file)
2. SECOND: Check project-specific documentation (README.md, docs/)
3. THIRD: Follow standard best practices

---

## 📋 Project-Specific Configuration

**WHERE TO FIND PROJECT INFORMATION:**
Look for these files in priority order:

1. **PROJECT_ANALYSIS.md** - Primary project documentation (if exists)
   - Current feature status
   - Database schemas
   - API documentation
   - Known issues and solutions
   - Development priorities
2. **README.md** - Basic project overview
3. **docs/** folder - Detailed documentation
4. **.env.example** - Required environment variables

**TO CUSTOMIZE THIS FOR YOUR PROJECT:**
Create or update `PROJECT_ANALYSIS.md` with:

- Project name and description
- Current implementation status
- Technology stack specifics
- Database configuration
- Business rules and domain logic
- Known issues and their solutions
- Feature completion tracking
- Architecture decisions

**IMPORTANT FOR AI ASSISTANTS:**

- ALWAYS check PROJECT_ANALYSIS.md FIRST for project state
- This is the single source of truth for project-specific information
- Update this file when implementing new features
- Don't create separate analysis documents

This CLAUDE.md file contains UNIVERSAL best practices that apply to ALL projects.

---

## 🚀 CI/CD Configuration

**This project has automated CI/CD configured:**

### GitHub Actions

- **Location**: `.github/workflows/ci.yml`
- **Runs**: On every push and pull request
- **Jobs**: Security, Quality, Tests, Build
- **Status**: Check Actions tab in GitHub

### Vercel Deployment

- **Auto-deploys**: On push to main branch
- **Preview deploys**: On every PR
- **Config**: `vercel.json`

## 🚨 CRITICAL REPOSITORY RULES 🚨

### 1. CLEAN REPOSITORY STRUCTURE MUST BE MAINTAINED!

**The repository has been professionally cleaned and organized. DO NOT clutter it.**

❌ **NEVER CREATE these files in root:**

- Test files (test-_.html, test-_.js, _.test._, _.spec._)
- SQL files (\*.sql) except in designated migration folders
- Analysis documents (_\_ANALYSIS.md, _\_ASSESSMENT.md, \*\_TODO.md)
- Build artifacts (\*.tsbuildinfo, dist/, build/)
- Multiple lock files (keep only one: package-lock.json OR yarn.lock OR pnpm-lock.yaml)
- Temporary files (_.tmp, _.temp, \*.bak)

✅ **ALWAYS:**

1. Put documentation in `docs/` folder
2. Keep test files in `__tests__/` or `e2e/`
3. Check `.gitignore` before creating files
4. Maintain clean root directory (~15 files max)

### 2. DOCUMENTATION STRUCTURE

📁 **Proper Documentation Structure:**

```
docs/
├── api/              # API documentation
├── architecture/     # Architecture decisions and diagrams
├── deployment/       # Deployment guides
├── development/      # Development guides
└── testing/          # Test documentation
```

✅ **ALWAYS DO:**

1. **Check existing documentation first** before creating new docs
2. **Update existing docs** rather than creating duplicates
3. **Place new docs in appropriate `docs/` subfolder**
4. **Keep root directory clean** - only README.md and essential configs

## 📂 File Structure Guidelines

### Recommended Project Structure:

```
project-root/              # ~15 files in root MAX
├── src/                  # Source code
│   ├── components/      # UI components
│   ├── services/        # Business logic
│   ├── utils/           # Helper functions
│   ├── hooks/           # Custom hooks
│   ├── types/           # TypeScript types
│   └── styles/          # Global styles
├── public/              # Static assets
├── tests/               # Test files
│   ├── unit/           # Unit tests
│   ├── integration/    # Integration tests
│   └── e2e/            # End-to-end tests
├── docs/                # Documentation
├── scripts/             # Build/utility scripts
├── .github/             # GitHub configs
└── [config files]       # Essential configs only
```

### Root Directory Rules:

- Maximum ~15 files in root
- Only essential configs (package.json, tsconfig.json, .gitignore, etc.)
- NO source code, test files, or temporary files
- Documentation in `docs/` except README.md

## 📚 Documentation Structure

### Primary Document (ALWAYS USE THIS):

- **PROJECT_ANALYSIS.md** - Complete project documentation with:
  - Current feature status and completion tracking
  - Database schemas and migrations
  - UI/UX issues and fixes
  - API endpoint documentation
  - Common issues and solutions
  - Security considerations
  - Testing strategy
  - Deployment guide
  - Version history

### Other Files (DO NOT DUPLICATE):

- **CLAUDE.md** - This file, quick reference for AI assistants
- **.env.local.example** - Environment variable template
- **package.json** - Dependencies and scripts

### Files to AVOID CREATING (use PROJECT_ANALYSIS.md instead):

- Separate feature assessment documents
- Individual analysis files per feature
- Multiple documentation files for the same information
- Any redundant analysis documents

---

## 🎯 Quick Reference for Common Tasks

### When Asked About Project Status

- Always check PROJECT_ANALYSIS.md first
- Look for current implementation status
- Review feature completion tracking
- Check known issues section

### When Fixing Issues

Check PROJECT_ANALYSIS.md Section: "Common Issues & Solutions"

### When Adding Features

Check PROJECT_ANALYSIS.md Section: "Development Priorities"

---

## 🚫 AVOIDING REDUNDANCY & DUPLICATE CODE

### CRITICAL: Code Reuse Principles

#### 1. BEFORE Writing Any Code:

```
1. Search for existing implementations:
   - Check lib/supabase/ for database services
   - Check components/ for UI components
   - Check lib/utils/ for helper functions
   - Use grep/search for similar functionality

2. Extend existing code instead of duplicating:
   - Found a similar service? Extend BaseService
   - Found a similar component? Create a variant
   - Found a similar function? Add parameters for flexibility
```

#### 2. Service Layer Pattern (USE THIS!):

```typescript
// ✅ GOOD: Extend base classes for common functionality
import { BaseService } from "@/services/base"

class UserService extends BaseService {
  // Inherits: error handling, validation, logging
}

// ❌ BAD: Duplicating logic everywhere
class UserService {
  async getUser() {
    try {
      /* duplicate code */
    } catch {
      /* duplicate error handling */
    }
  }
}
```

#### 3. Component Reuse:

```typescript
// ✅ GOOD: Use existing components
import { LoadingSpinner } from '@/components/ui/loading';
import { ErrorBoundary } from '@/components/error-boundary';

// ❌ BAD: Creating duplicate components
<div>Loading...</div>  // Don't do this!
```

#### 4. Utility Functions:

```typescript
// ✅ GOOD: Use centralized utilities
import { formatDate, parseJSON } from "@/utils/helpers"

// ❌ BAD: Inline utility logic
const formatted = new Date().toLocaleDateString() // Avoid!
```

### DRY (Don't Repeat Yourself) Checklist:

Before implementing ANY feature:

- [ ] Did I search for existing similar code?
- [ ] Can I extend an existing service/component?
- [ ] Am I using centralized error handling?
- [ ] Am I using shared utility functions?
- [ ] Am I following established patterns?

### Common Redundancy Patterns to AVOID:

#### ❌ NEVER DO:

1. **Duplicate API calls** - Use service layer
2. **Duplicate error handling** - Extend BaseService
3. **Duplicate loading states** - Use OptimizedLoading
4. **Duplicate date formatting** - Use utils
5. **Duplicate validation** - Use shared validators
6. **Duplicate types** - Use lib/types
7. **Duplicate styles** - Use Tailwind utilities

#### ✅ ALWAYS DO:

1. **Search first, code second**
2. **Extend, don't duplicate**
3. **Centralize common logic**
4. **Use composition over duplication**
5. **Follow established patterns**

### Refactoring for Redundancy:

When you spot duplicate code:

1. Extract to shared utility/service
2. Update all instances to use shared code
3. Test thoroughly
4. Document the shared functionality

---

## 🔧 Component Refactoring Best Practices

### Component Size Limits (MANDATORY)
- **Maximum lines per component**: 300 lines
- **Maximum lines per service**: 500 lines
- **Maximum lines per utility function**: 100 lines

### Refactoring Pattern for Oversized Components

When a component exceeds 300 lines, use this pattern:

#### 1. **Analyze Structure**
```bash
# Check line count
wc -l src/components/sections/ComponentName.tsx

# Find logical divisions
grep -n "^function\|^const.*=.*=>" ComponentName.tsx
```

#### 2. **Split into Three Parts**
```
Before (565 lines):
└── ComponentName.tsx (everything mixed together)

After:
├── ComponentName.tsx (main component, <300 lines)
├── SubComponent.tsx (extracted sub-component)
└── data/component-data.tsx (data and types)
```

#### 3. **Data Files with JSX**
```typescript
// ⚠️ IMPORTANT: Files with JSX must use .tsx extension
// data/component-data.tsx (NOT .ts)
import { Icon } from 'lucide-react'

export const data = [
  { icon: <Icon size={20} />, text: 'Item' }
]
```

#### 4. **Import Patterns**
```typescript
// ✅ CORRECT: No file extension in imports
import { data } from '@/data/component-data'

// ❌ WRONG: Don't include extension
import { data } from '@/data/component-data.tsx'
```

### Personal Files Management

#### Creating a Personal Folder
```bash
# Create personal folder for non-code files
mkdir personal

# Move personal documents
mv *.docx *.pdf resume.xml personal/

# Add to .gitignore
echo "personal/" >> .gitignore
```

#### Session Documentation
```bash
# Store session-specific docs separately
mkdir -p docs/session-notes
mv *_AUDIT.md *_SUMMARY.md docs/session-notes/
```

### Common Refactoring Issues & Solutions

#### Issue: Build fails after creating data file
**Cause**: JSX in .ts file
**Solution**: Rename to .tsx
```bash
mv src/data/component-data.ts src/data/component-data.tsx
```

#### Issue: Import path error
**Cause**: File extension in import
**Solution**: Remove extension from import statement

#### Issue: Git credentials fail on Windows
**Solutions**:
1. Use Personal Access Token (recommended)
2. Use GitHub Desktop
3. Fix credential manager:
```bash
git config --global credential.helper wincred
```

### Refactoring Checklist

Before refactoring:
- [ ] Check current line count
- [ ] Identify logical component boundaries
- [ ] Plan data extraction
- [ ] Consider reusable sub-components

During refactoring:
- [ ] Extract data and types first
- [ ] Create sub-components for complex sections
- [ ] Use .tsx for files with JSX
- [ ] Keep imports clean (no extensions)

After refactoring:
- [ ] All components < 300 lines
- [ ] Run build to verify: `npm run build`
- [ ] Test functionality: `npm run dev`
- [ ] Commit with clear message

---

## 🧹 MAINTAINING CLEAN REPOSITORY

### When Creating Files:

1. **Ask yourself**: Does this belong in root? (Probably not!)
2. **Check for existing similar files first!**
3. **Documentation?** → Put in `docs/` folder
4. **Test file?** → Put in `__tests__/` or `e2e/`
5. **SQL file?** → Only in `supabase/migrations/`
6. **Temporary file?** → Don't commit it!

### Before ANY commit:

```bash
# Check what you're adding
git status

# If you see test-*.html, *.sql, or temp files:
# DON'T COMMIT THEM!
```

### Repository Standards:

- **Root directory**: ~15 files maximum
- **Documentation**: Organized in `docs/` subfolders
- **Tests**: In proper test directories
- **Build artifacts**: Never committed
- **Professional appearance**: Clean for sharing

Remember:

- **PROJECT_ANALYSIS.md is the ONLY analysis document that matters!**
- **Keep the repository CLEAN and PROFESSIONAL!**

---

## 🔀 GitHub Workflow & Collaboration Standards

### Branch Naming Conventions

```
feature/[ticket-id]-brief-description
bugfix/[ticket-id]-brief-description
hotfix/[ticket-id]-brief-description
chore/brief-description
refactor/brief-description
```

### Commit Message Format (Conventional Commits)

```
feat: add new feature
fix: resolve bug
docs: update documentation
style: formatting changes
refactor: code restructuring
test: add/update tests
perf: performance improvements
chore: maintenance tasks
ci: CI/CD changes
build: build system changes
```

### Pull Request Requirements

- [ ] Descriptive title following format: `[Type] Brief description`
- [ ] Links to related issues/tickets
- [ ] All CI checks passing
- [ ] Tests added/updated for changes
- [ ] Documentation updated if needed
- [ ] No console.logs or debug code
- [ ] Follows code style guidelines
- [ ] Self-reviewed for redundancy

### Code Review Guidelines

- Check for code duplication
- Verify error handling
- Ensure proper TypeScript types
- Validate security considerations
- Test functionality locally
- Review performance impact

---

## 📊 Code Quality Standards

### TypeScript Requirements

```typescript
// tsconfig.json should include:
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true
  }
}
```

### Naming Conventions

- **Files**: kebab-case (e.g., `user-service.ts`)
- **Components**: PascalCase (e.g., `UserProfile.tsx`)
- **Functions/Variables**: camelCase (e.g., `getUserData`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRIES`)
- **Interfaces/Types**: PascalCase with 'I' or 'T' prefix (e.g., `IUser`, `TResponse`)

### Import Order

1. React/Next.js imports
2. Third-party libraries
3. Internal aliases (@/...)
4. Relative imports
5. Style imports

### File Size Limits

- Components: < 300 lines
- Services: < 500 lines
- Utils: < 100 lines per function
- Split larger files into smaller modules

---

## 🧪 Testing Requirements

### Coverage Thresholds

- Minimum overall: 70%
- New code: 80%
- Critical paths: 90%
- Utilities: 95%

### Test Structure

```typescript
describe("ComponentName", () => {
  describe("functionality group", () => {
    it("should do specific behavior", () => {
      // Arrange
      // Act
      // Assert
    })
  })
})
```

### Testing Checklist

- [ ] Unit tests for utilities
- [ ] Integration tests for services
- [ ] Component tests with RTL
- [ ] E2E tests for critical flows
- [ ] Error cases tested
- [ ] Edge cases covered
- [ ] Loading states tested
- [ ] Mock data follows real schema

---

## 🔒 Security Best Practices

### Input Validation

- Validate ALL user inputs
- Use Zod/Yup for schema validation
- Sanitize HTML content
- Validate file uploads (type, size)

### Database Security

- Use parameterized queries ONLY
- Never concatenate SQL strings
- Validate data types before queries
- Use Row Level Security (RLS) in Supabase

### Authentication & Authorization

- Store tokens securely (httpOnly cookies)
- Implement CSRF protection
- Use secure headers (CSP, HSTS)
- Rate limit API endpoints
- Validate permissions on each request

### Vulnerability Scanning Requirements

#### 🤖 Automated Security (CI/CD Active!)

**AUTOMATIC CHECKS ON EVERY PUSH/PR:**

- ✅ **GitHub Actions CI** (Remote):
  - Full security audit (all severity levels)
  - Secret scanning with Trufflehog
  - Code quality checks (lint, TypeScript)
  - Test coverage reporting to Codecov
  - Build verification
  - Bundle size analysis
  - Dependency checking with depcheck

#### Manual Security Checks (As Backup)

**IF AUTOMATION FAILS - Run Manually:**

```bash
# Quick security check
npm audit

# Fix vulnerabilities
npm audit fix

# Check for secrets
git diff --staged | grep -E "(api_key|apikey|secret|password|token)" -i
```

**WEEKLY MAINTENANCE:**

```bash
# Check for outdated packages
npm outdated

# Update dependencies safely
npm update --save

# Verify everything still works
npm test && npm run build
```

**OPTIONAL - Enhanced Security Tools:**

```bash
# Install once (optional but recommended)
npm install -g snyk
npm install -g npm-check-updates

# Run periodically
snyk test                       # Better vulnerability database
ncu -u                          # Check latest versions
npx depcheck                    # Find unused dependencies
npx license-checker --summary   # License compliance
```

#### Security Rules for Manual Review

- ✅ **MUST FIX** before committing:
  - Critical vulnerabilities
  - High vulnerabilities in production dependencies
  - Exposed secrets or API keys
- ⚠️ **SHOULD FIX** within a week:
  - Medium vulnerabilities
  - Outdated major versions
- 💡 **CONSIDER FIXING** monthly:
  - Low vulnerabilities
  - Dev dependency issues
  - Minor version updates

#### Quick Security Checklist

Before pushing code, ask yourself:

- [ ] Did I run `npm audit`?
- [ ] Are there any critical/high vulnerabilities?
- [ ] Did I accidentally commit any secrets/API keys?
- [ ] Are my dependencies reasonably up-to-date?

#### Handling Vulnerabilities

1. **Critical/High**: Fix immediately, block deployments
2. **Medium**: Fix within 7 days
3. **Low**: Fix within 30 days
4. **Dependencies**: Update or find alternatives
5. **Can't fix**: Document in `SECURITY.md` with mitigation

---

## ⚡ Performance Standards

### Performance Budget

- Bundle size: < 500KB (initial)
- Chunk size: < 200KB
- First Contentful Paint: < 1.5s
- Time to Interactive: < 3.5s
- Lighthouse Score: > 85

### Performance Optimization Workflow

#### **Step 1: Identify Issues**
```bash
# Check for unused dependencies
npx depcheck

# Analyze bundle size
npm run analyze

# Check current performance metrics
npm run build
```

#### **Step 2: Quick Wins First**
1. Remove unused dependencies
2. Add React.memo() to heavy components
3. Move static data outside components
4. Add loading states for slow operations

#### **Step 3: Test Each Change**
```bash
# After each optimization
npm run build
npm run dev  # Manual testing
```

### React Performance Optimization (CRITICAL)

#### **Always Use React.memo() for:**
- Components with Framer Motion animations
- Components that receive props but don't change often
- List item components
- Modal/Dialog components

#### **Memoization Pattern (MUST FOLLOW):**
```typescript
// ✅ CORRECT: Memo with memoized values
import { memo, useMemo, useCallback } from 'react'

function MyComponent({ data }) {
  // Memoize expensive computations
  const processedData = useMemo(() =>
    expensiveOperation(data), [data])

  // Memoize callbacks to prevent child re-renders
  const handleClick = useCallback((id) => {
    // handle click
  }, [])

  // Memoize animation variants
  const animationVariants = useMemo(() => ({
    initial: { opacity: 0 },
    animate: { opacity: 1 }
  }), [])

  return <div>...</div>
}

export default memo(MyComponent)
```

#### **Data Outside Components:**
```typescript
// ✅ CORRECT: Static data outside component
const staticData = [/* large array */]

function Component() {
  const data = useMemo(() => staticData, [])
}

// ❌ WRONG: Data inside component
function Component() {
  const data = [/* recreated every render */]
}
```

### Optimization Requirements

- Lazy load components with dynamic imports
- Optimize images (WebP, proper sizing)
- Use React.memo for expensive components
- Implement virtual scrolling for long lists
- Cache API responses appropriately
- Debounce/throttle user inputs

### Bundle Analysis

```bash
# Analyze bundle size
npm run analyze

# Check for duplicates
npm run find-duplicates

# Check for unused dependencies
npx depcheck
```

---

## ♿ Accessibility Standards

### WCAG 2.1 AA Compliance

- Color contrast ratio: 4.5:1 (normal text), 3:1 (large text)
- All interactive elements keyboard accessible
- Focus indicators visible and clear
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text for all images
- ARIA labels for icon buttons
- Form labels associated with inputs
- Error messages linked to fields

### Testing Accessibility

```bash
# Run accessibility tests
npm run test:a11y

# Use screen reader testing
# Test keyboard navigation
# Check with browser DevTools
```

---

## 📝 Documentation Standards

### Code Documentation

```typescript
/**
 * Brief description of function purpose
 * @param {string} param1 - Description of param1
 * @param {number} param2 - Description of param2
 * @returns {Promise<Result>} Description of return value
 * @throws {Error} Description of possible errors
 * @example
 * const result = await functionName('value', 123);
 */
```

### README Requirements

- Project overview
- Setup instructions
- Environment variables
- Available scripts
- Deployment guide
- Contributing guidelines
- License information

---

## 🤖 AI Assistant Development Patterns

### Conversational AI Best Practices

#### **Core Principles**
1. **Accuracy First** - Only state verifiable facts
2. **Storytelling > Lists** - Transform data into narratives
3. **Guardrails Required** - Implement strict boundaries
4. **Personality Matters** - Add character to loading/error states

#### **System Prompt Structure**
```typescript
const systemPrompt = `
CRITICAL GUARDRAILS:
• Only state verifiable facts
• Never fabricate details
• Stay within scope

PERSONALITY:
[Define the assistant's character]

CONVERSATION STYLE:
• Tell stories, not lists
• Be conversational
• Ask engaging follow-ups
`
```

#### **Loading States for Slow Operations**
```typescript
// Pattern for any slow-loading content (iframes, API calls, etc.)
const [isLoading, setIsLoading] = useState(true)

return (
  <>
    {isLoading && (
      <div className="loading-overlay">
        <Loader className="animate-spin" />
        <p>Loading content...</p>
        <p className="text-sm">This may take a few seconds</p>
      </div>
    )}
    <iframe onLoad={() => setIsLoading(false)} />
  </>
)
```

#### **Dynamic Loading Messages**
```typescript
const loadingMessages = [
  "Gathering information...",
  "Processing your request...",
  "Almost there...",
]
const randomMessage = loadingMessages[Math.floor(Math.random() * loadingMessages.length)]
```

## 🚨 Error Handling

### Error Boundary Implementation

```typescript
// Every major section should have error boundary
<ErrorBoundary fallback={<ErrorFallback />}>
  <Component />
</ErrorBoundary>
```

### Logging Standards

```typescript
// Use structured logging
logger.error("Operation failed", {
  operation: "createUser",
  userId: user.id,
  error: error.message,
  stack: error.stack,
  timestamp: new Date().toISOString(),
})
```

### User-Facing Errors

- Clear, actionable messages
- No technical jargon
- Suggest next steps
- Provide support contact

---

## 📦 Repository Maintenance

### Common Files That Should NOT Be in Root

- Test files (`*.test.*`, `*.spec.*`, `test-*.*`)
- Database files (`*.sql`, `*.db`, migrations)
- Generated types (`*-types.ts`, `*.d.ts` except config types)
- Scripts (unless they're npm scripts)
- Temporary files (`*.tmp`, `*.temp`, `nul`)

### Maximum Files in Root

- Configuration files only
- Maximum 15 files
- No test files
- No SQL files
- No temporary files

### Essential .gitignore Configuration

**MUST be in .gitignore:**
```gitignore
# Dependencies
node_modules/
.pnp
.pnp.js
.yarn/

# Testing
coverage/
.nyc_output/
playwright-report/
test-results/

# Build outputs
.next/
out/
dist/
build/
*.tsbuildinfo

# Environment files
.env*
!.env.example
!.env.*.example

# IDE files
.vscode/
.idea/
*.swp
*.swo

# OS files
.DS_Store
Thumbs.db

# Logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Temporary files
*.tmp
*.temp
*.bak
tmp/
temp/

# CI/CD
.vercel
.turbo/

# Project-specific
*.sql
!migrations/*.sql
test-*.html
test-*.js
```

**NEVER commit:**
- API keys or secrets
- Personal configuration files
- Generated files (build outputs)
- Dependencies (node_modules)
- Test coverage reports
- IDE-specific settings

---

## 📋 Implementation Planning (MANDATORY)

### Before Writing ANY Code for New Features/Changes:

**STOP! Create an implementation plan FIRST:**

```markdown
## Implementation Plan: [Feature Name]

### 1. Objective

- Clear description of what needs to be accomplished
- Success criteria

### 2. Current State Analysis

- [ ] Search for existing similar implementations
- [ ] Identify reusable components/services
- [ ] Note potential conflicts or dependencies

### 3. Technical Approach

- Architecture decisions
- Components/services to create or modify
- Data flow and state management
- Database changes required

### 4. Implementation Steps

1. [ ] Step 1: Description
2. [ ] Step 2: Description
3. [ ] Step 3: Description
       (Break down into small, testable chunks)

### 5. Testing Strategy

- Unit tests needed
- Integration tests needed
- E2E test scenarios

### 6. Rollback Plan

- How to revert if issues occur
- Feature flags needed?

### 7. Estimated Impact

- Performance implications
- Bundle size changes
- Breaking changes
- User experience changes
```

### When to Create Implementation Plans:

- ✅ **ALWAYS for**: New features, refactoring, breaking changes, database migrations
- ⚠️ **OPTIONAL for**: Bug fixes < 10 lines, typo corrections, simple style changes
- 🚫 **SKIP for**: Documentation updates, comment additions

### Plan Review Checklist:

- [ ] Have I searched for existing similar code?
- [ ] Can I extend existing services/components?
- [ ] Have I considered error handling?
- [ ] Is my approach the simplest solution?
- [ ] Will this create technical debt?
- [ ] Have I considered performance impact?

**Remember: 5 minutes of planning saves hours of refactoring!**

---

## 🔄 Incremental Implementation (REQUIRED)

### The Golden Rule: NEVER Break the Build!

**Every change must follow incremental implementation:**

### 1. Small, Atomic Commits

```bash
# ✅ GOOD: One logical change per commit
git add components/UserProfile.tsx
git commit -m "feat: add user avatar to profile"

# ❌ BAD: Multiple unrelated changes
git add .
git commit -m "update everything"
```

### 2. Implementation Strategy

```markdown
Instead of implementing all at once:
❌ Build entire feature → Test → Debug everything → Deploy

Use incremental approach:
✅ Step 1: Create basic structure → Commit → Test
✅ Step 2: Add core functionality → Commit → Test  
✅ Step 3: Add validation → Commit → Test
✅ Step 4: Add error handling → Commit → Test
✅ Step 5: Add UI polish → Commit → Test
```

### 3. Each Increment MUST:

- [ ] **Keep the app functional** - No breaking changes
- [ ] **Be independently testable** - Can verify this step works
- [ ] **Add value** - Each step improves the codebase
- [ ] **Be revertable** - Can rollback without losing other work

### 4. Incremental Workflow

```typescript
// Phase 1: Structure (Commit 1)
export const NewFeature = () => {
  return <div>New Feature Placeholder</div>;
};

// Phase 2: Basic Functionality (Commit 2)
export const NewFeature = () => {
  const [data, setData] = useState([]);
  return <div>{data.map(item => <div key={item.id}>{item.name}</div>)}</div>;
};

// Phase 3: Data Fetching (Commit 3)
export const NewFeature = () => {
  const [data, setData] = useState([]);
  useEffect(() => {
    fetchData().then(setData);
  }, []);
  return <div>{data.map(item => <div key={item.id}>{item.name}</div>)}</div>;
};

// Phase 4: Error Handling (Commit 4)
// Phase 5: Loading States (Commit 5)
// Phase 6: Polish & Optimization (Commit 6)
```

### 5. Testing Between Increments

```bash
# After EVERY increment:
npm run lint        # Must pass
npm run type-check  # Must pass
npm run test        # Must pass
npm run dev         # Manual verification

# Only proceed to next increment if all pass!
```

### 6. Benefits of Incremental Implementation

- ✅ **Easier debugging** - Know exactly which change broke something
- ✅ **Better code review** - Smaller, focused changes
- ✅ **Safer deployment** - Can deploy partial features behind flags
- ✅ **Reduced risk** - Can stop or pivot at any increment
- ✅ **Cleaner history** - Git history tells the story

### 7. When to Commit

Commit when you have:

- Added a new component (even if empty)
- Implemented one function/method
- Fixed one specific bug
- Added tests for one feature
- Refactored one module
- Updated documentation

### 8. Red Flags (AVOID THESE!)

- 🚫 "Work in progress" commits with broken code
- 🚫 Giant commits with 20+ file changes
- 🚫 Mixing features and refactoring in one commit
- 🚫 Committing commented-out code
- 🚫 "Fixed stuff" commit messages

**Remember: If you can't deploy after any commit, you're not being incremental enough!**

---

## 🎯 Development Priorities

When working on this codebase, prioritize in this order:

1. **Fix breaking bugs** - Production issues first
2. **Security vulnerabilities** - Address immediately
3. **Performance issues** - User experience critical
4. **Test coverage** - Maintain quality
5. **Code cleanup** - Reduce technical debt
6. **New features** - After stability ensured
7. **Documentation** - Keep updated

---

## 📌 Quick Reference Commands

### Common Development Commands:

```bash
# Package Manager (npm/yarn/pnpm)
npm install          # Install dependencies
npm run dev          # Start dev server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run linting
npm run test         # Run tests

# Code Quality
npm run lint:fix     # Auto-fix linting issues
npm run format       # Format code
npm run type-check   # TypeScript validation
npm audit           # Security audit

# Testing
npm test            # Run tests
npm run test:watch  # Run tests in watch mode
npm run test:coverage # Generate coverage report
npm run test:e2e    # Run end-to-end tests

# Git Workflow
git status          # Check changes
git add .           # Stage changes
git commit -m "..." # Commit with message
git push           # Push to remote
git pull           # Pull from remote
```

---

## ⚠️ FINAL REMINDERS FOR AI ASSISTANTS

1. **ALWAYS** search for existing code before creating new files
2. **NEVER** duplicate functionality - extend existing code
3. **ALWAYS** run lint and type-check before marking tasks complete
4. **NEVER** commit without testing your changes
5. **ALWAYS** update documentation when changing functionality
6. **NEVER** add files to root directory without justification
7. **ALWAYS** follow the established patterns in the codebase
8. **NEVER** use 'any' type without explicit justification
9. **ALWAYS** handle errors appropriately
10. **NEVER** log sensitive information

This document is your contract with the codebase. Follow it strictly.
