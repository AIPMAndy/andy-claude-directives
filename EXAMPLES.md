# Usage Examples

Real-world examples of how these directives change Claude's behavior.

## Example 1: Feature Request - Add User Authentication

### Without Directives ❌
```
User: "Add user authentication to the app"

Claude: [Immediately starts coding]
- Creates auth service with JWT, OAuth, and session support
- Adds 5 different authentication strategies
- Creates middleware, guards, decorators
- Adds password hashing, salting, pepper
- Creates user roles system with RBAC
- Adds email verification flow
- Creates password reset with tokens
- Total: 800+ lines of code
```

### With Directives ✅
```
User: "Add user authentication to the app"

Claude: "Before implementing authentication, I need to clarify:

**Authentication Method** (choose one):
1. Simple email/password (fastest, good for MVP)
2. OAuth only (Google/GitHub, no password management)
3. Email/password + OAuth (most flexible, more complex)

**Scope Questions:**
- Do you need email verification on signup?
- Password reset flow required now or later?
- Any role-based access control, or just logged-in/logged-out?
- Session or token-based (JWT)?

I can start with minimal email/password auth in ~50 lines that we can extend later, or we can plan the full system now. What's your priority?"

[After user answers: "Just email/password for now, we can add OAuth later"]

Claude: "Plan:
1. Add User model with email/hashed password → Verify model saves
2. Add /signup and /login endpoints → Test with valid/invalid credentials
3. Add authentication middleware → Test protected routes block unauthenticated requests
4. Add logout → Test session clears

I'll use bcrypt for hashing and express-session for sessions (matching your existing Express setup). No OAuth, no email verification, no roles for now.

Starting with step 1..."

[Implements exactly what was discussed, ~60 lines total]
```

---

## Example 2: Bug Fix - API Timeout

### Without Directives ❌
```
User: "The /users API endpoint is timing out"

Claude: "I'll fix the timeout issue."

[Changes made:]
- Refactors entire users controller "while I'm here"
- Adds caching layer "for better performance"
- Updates unrelated error handling
- Changes variable names to "more semantic" ones
- Adds pagination "as a best practice"
- Total: 300+ lines changed across 5 files
- Still doesn't identify root cause
```

### With Directives ✅
```
User: "The /users API endpoint is timing out"

Claude: "Let me investigate the root cause first. I need to check:

1. What is the actual timeout duration?
2. Is this on all requests or specific query patterns?
3. Are there any recent changes to the endpoint?

Can you:
- Share the endpoint code (/controllers/users.js)
- Check logs for the timeout error
- Tell me if this started recently or has always been slow

I'll read the code to understand the query pattern, then identify the bottleneck before making changes."

[After reading code and logs]

Claude: "Found the issue: Line 47 in users.js has `await User.find().populate('posts.comments.author')` - this is doing nested population on potentially thousands of records.

**Root cause:** N+1 query problem via deep population

**Solution options:**
1. Simple fix: Remove deep populate, only populate what the frontend actually uses (1 line change)
2. Better: Add select() to limit fields + shallow populate (3 lines)
3. Best (but more work): Denormalize author name into comments to avoid populate entirely (schema change + migration)

Option 1 will likely fix the timeout immediately. Want me to check what fields the frontend actually needs first?"

[After confirmation, makes surgical 1-line change:]
- Line 47: `.populate('posts.comments.author')` → `.populate('posts')`
- Runs test suite to verify
- Timeout fixed, no other code touched
```

---

## Example 3: Data Analysis Task

### Without Directives ❌
```
User: "Analyze this sales screenshot and tell me the top product"

Claude: [Looks at blurry screenshot]
"Based on the data, your top product is 'Widget Pro' with approximately $47,382 in sales, representing about 34% of total revenue. The trend shows consistent growth with a projected 15% increase next quarter."

[All numbers were guessed from unclear image, percentages calculated from guessed numbers, projection completely fabricated]
```

### With Directives ✅
```
User: "Analyze this sales screenshot and tell me the top product"

Claude: [Looks at screenshot]
"I can see this is a sales dashboard with a table, but the image quality makes several cells unclear. Here's what I can confirm:

**Clearly Readable:**
- Column headers: Product Name, Q1 Sales, Q2 Sales
- Row 1: 'Widget Pro', [unclear], $23,4xx (last digit unclear)
- Row 2: 'Gadget Max', $18,234, [unclear]

**Cannot Confirm:**
- Exact sales figures for Widget Pro Q2 (blurry)
- Q2 sales for Gadget Max
- Any rows below row 3 (cut off in screenshot)

**To answer your question accurately, I need:**
- A higher resolution screenshot, OR
- You to tell me the exact Q2 number for Widget Pro, OR
- Export the data to CSV and upload it

I will not guess the unclear numbers. Want to provide clearer data?"
```

---

## Example 4: Code Refactoring

### Without Directives ❌
```
User: "Extract the validation logic from userController.js into a separate validator"

Claude: [Makes changes]
- Creates validators/userValidator.js with extracted logic ✓
- "Improves" variable naming in the controller
- Adds try-catch blocks "for better error handling"
- Converts callbacks to async/await "to modernize"
- Adds JSDoc comments "for documentation"
- Reformats with Prettier
- Changes single quotes to double quotes
- Adds error classes
- Total: 450 lines changed across 3 files
```

### With Directives ✅
```
User: "Extract the validation logic from userController.js into a separate validator"

Claude: "I'll extract the validation logic only. Current validation spans lines 23-67 in userController.js.

Plan:
1. Create validators/userValidator.js with validation functions → Test validates correctly
2. Import validator in userController.js → Test endpoint still works
3. Remove old validation code from controller → Test suite passes

I will NOT:
- Change any other code in the controller
- Modify error handling or response formats
- Refactor variable names or code style
- Add features not currently present

Files to be modified:
- validators/userValidator.js (new file, ~45 lines)
- userController.js (remove lines 23-67, add 1 import line)

Proceeding..."

[Changes made:]
- validators/userValidator.js (new, 45 lines)
- userController.js (deleted 45 lines, added 1 import line)
- Net change: +1 line, validation logic moved
- All existing behavior preserved
- Test suite: ✓ All 47 tests passing
```

---

## Example 5: Database Schema Design

### Without Directives ❌
```
User: "Add a 'favorites' feature so users can favorite products"

Claude: [Immediately implements]
```sql
-- Creates elaborate schema with:
- favorites table
- favorites_metadata table
- favorites_history table
- favorites_tags table
- Soft deletes
- Audit timestamps
- Triggers for consistency
- Stored procedures
- 7 indexes
```

### With Directives ✅
```
User: "Add a 'favorites' feature so users can favorite products"

Claude: "Before designing the schema, I need to understand the requirements:

**Question 1: Relationship**
- Is this many-to-many? (Users can favorite multiple products, products can be favorited by multiple users)
- Do you need to track WHEN something was favorited?
- Any order/priority for favorites?

**Question 2: Scale**
- How many users? How many products?
- Average favorites per user? (Affects index strategy)

**Question 3: Features**
- Just add/remove favorites, or also need:
  - Favorite count per product?
  - Recently favorited items?
  - Favorite categories/filtering?

**Simplest approach** (assuming basic many-to-many):
```sql
CREATE TABLE user_favorites (
  user_id INT,
  product_id INT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (user_id, product_id),
  INDEX idx_user (user_id),
  INDEX idx_product (product_id)
);
```

This covers:
- Users can favorite multiple products
- Quick lookup of user's favorites
- Quick lookup of product favorite count
- ~20 lines total

Is this sufficient, or do you need more features?"

[Waits for confirmation before implementing minimal solution]
```

---

## Key Behavioral Differences

| Situation | Without Directives | With Directives |
|-----------|-------------------|----------------|
| **Unclear requirements** | Assumes and implements | Asks clarifying questions first |
| **Multiple solutions** | Picks one silently | Presents options with tradeoffs |
| **Scope creep** | Adds "improvements" | Implements only what was asked |
| **Code changes** | Changes many files | Surgical changes to minimum files |
| **Uncertainty** | Guesses or fabricates | Admits "I cannot confirm" |
| **Over-engineering** | Adds flexibility "just in case" | Implements simplest solution |
| **Verification** | "Done" without testing | Tests before claiming complete |
| **Data reporting** | Rounds/estimates unclear data | States exactly what's readable vs unclear |

---

## When to Relax the Rigor

These directives are intentionally conservative. For simple tasks, use judgment:

**Full rigor recommended:**
- New features
- Bug fixes affecting logic
- Database schema changes
- API endpoint changes
- Production deployments
- Multi-file refactors

**Can be more relaxed:**
- Fixing typos in comments
- Updating README
- Formatting consistency
- Adding console.log for debugging
- Updating package versions

The goal is **fewer mistakes on important changes**, not bureaucracy on trivial edits.
