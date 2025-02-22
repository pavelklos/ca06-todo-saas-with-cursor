I'll help create a step-by-step plan to add team-based todo functionality to the Base plan. Let's break this down into small, verifiable steps:

## Phase 1: Database Schema
1. Add Todo table to the existing Drizzle schema with:
   - id (auto-increment)
   - title (string)
   - description (string, optional)
   - completed (boolean)
   - teamId (foreign key to teams table)
   - createdBy (foreign key to users table)
   - createdAt (timestamp)
   - updatedAt (timestamp)

2. Create and test the migration to verify the table is created correctly

## Phase 2: Basic Backend Structure
1. Create database queries for todos:
   - Add query functions in `lib/db/queries.ts`
   - Test each query function individually

2. Add server actions for todos in `app/(dashboard)/actions.ts`:
   - Create basic CRUD functions
   - Add proper validation using Zod schemas
   - Test each action individually

## Phase 3: Basic Frontend - List View
1. Create todo list page at `app/(dashboard)/todos/page.tsx`:
   - Add basic table/list structure
   - Show loading states
   - Display todos from the database
   - Test that todos are displayed correctly

2. Add todo list to navigation:
   - Update dashboard layout
   - Add navigation link
   - Test navigation works

## Phase 4: Create Todo Functionality
1. Create "Add Todo" form component:
   - Basic form with title/description
   - Connect to create action
   - Add validation
   - Test form submission

2. Add role-based access control:
   - Restrict create functionality to owners
   - Test permissions work correctly

## Phase 5: Update Todo Functionality
1. Create edit todo component:
   - Add edit form
   - Connect to update action
   - Add validation
   - Test update functionality

2. Add role-based access:
   - Allow both owners and members to edit
   - Test permissions work

## Phase 6: Delete Todo Functionality
1. Add delete functionality:
   - Create delete button/confirmation
   - Connect to delete action
   - Test deletion works

2. Add role-based access:
   - Allow both owners and members to delete
   - Test permissions work

## Phase 7: UI Polish & Error Handling
1. Add proper error states:
   - Form validation errors
   - Server errors
   - Permission errors
   - Test all error scenarios

2. Add success notifications:
   - Show success messages
   - Add loading states
   - Test user feedback works

## Phase 8: Final Testing & Integration
1. End-to-end testing:
   - Test all CRUD operations
   - Test permissions
   - Test error handling
   - Verify UI/UX flow

2. Performance testing:
   - Test with multiple todos
   - Verify loading states
   - Check database queries

Would you like to start with Phase 1 and implement the database schema changes first?
