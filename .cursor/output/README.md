**_Below is a sample generated output by Cursor using the `commands/build-review.mdc` rule._**

# Build Review Report

**Project:** kebab-client

**Build Command:** `npm run build`

**Analysis Date:** 2025-03-27 14:21

### Executive Summary
The build process completed successfully but with several warnings that need attention. The main issues include React Hook dependency warnings, an outdated browserslist database, and import errors related to the 'cookie' module. While these issues don't prevent the build from completing, they should be addressed to improve code quality and prevent potential runtime issues.

### Build Status
- **Result:** Success with Warnings
- **Duration:** Completed in multiple stages
- **Exit Code:** 0
- **Build Artifacts Generated:** Yes

### Error Analysis
#### Critical Errors
No critical errors were found that prevented the build from completing.

#### Error Patterns
1. Cookie Module Import Issues:
   | Error Type | File | Description | Resolution |
   |---|---|---|---|
   | Import Error | app/api/organization-login/route.ts | 'cookie' does not contain a default export | Update import to use named exports |
   | Import Error | app/api/personal-login/route.ts | 'cookie' does not contain a default export | Update import to use named exports |

### Warning Analysis
#### Warning Summary
| Severity | Count | Category | Example |
|---|---|---|---|
| Medium | 14 | React Hook Dependencies | Missing dependencies in useEffect/useCallback hooks |
| Low | 1 | Tailwind Plugin | @tailwindcss/line-clamp plugin redundancy |
| Low | 1 | Browserslist | Outdated browserslist database |

#### Impact Assessment
1. React Hook Warnings:
   - Potential memory leaks from missing dependencies
   - Possible stale closures leading to bugs
   - May cause unnecessary re-renders

2. Configuration Warnings:
   - Tailwind CSS line-clamp plugin is now included by default
   - Browserslist database needs updating for optimal browser targeting

### Build Performance
#### Time Metrics
Build completed successfully with the following stages:
- Static page generation: 58/58 pages generated
- Middleware compilation
- Route compilation and optimization

#### Optimization Opportunities
1. Large page sizes that could be optimized:
   - /bsky: 135 kB
   - /kebabs/[uuid]: 14.6 kB
   - /settings/account: 22.7 kB

### Dependency Analysis
#### Dependency Health
- No outdated packages detected
- Browserslist database needs updating
- Tailwind CSS configuration needs cleanup

### Bundle Analysis
#### Size Metrics
Notable bundle sizes:
| Route | Size | First Load JS |
|---|---|---|
| /bsky | 135 kB | 421 kB |
| /kebabs/[uuid] | 14.6 kB | 787 kB |
| /settings/account | 22.7 kB | 200 kB |

Shared chunks:
- Total shared JS: 87.8 kB
- Largest chunk: fd9d1056-e6f034e282a692e3.js (53.6 kB)

### Action Items
1. **High Priority:**
   - Fix cookie module imports in login routes
   - Address React Hook dependency warnings
   - Update browserslist database: `npx update-browserslist-db@latest`

2. **Medium Priority:**
   - Remove @tailwindcss/line-clamp from plugins array in Tailwind config
   - Optimize large bundle sizes, especially in /bsky and /kebabs/[uuid] routes

3. **Low Priority:**
   - Review and optimize page sizes over 10 kB
   - Consider implementing code splitting for large routes

### Re-build Verification
**Result:** Success with warnings
**Remaining Issues:** 16 warnings total
- 14 React Hook dependency warnings
- 1 Tailwind configuration warning
- 1 Browserslist warning 