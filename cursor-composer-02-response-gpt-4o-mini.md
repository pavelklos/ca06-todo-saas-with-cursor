Here’s a step-by-step plan to add To-Do list functionality to the Base plan for your SaaS application. Each step is designed to be small and manageable, allowing for confirmation of success before proceeding to the next step.

## Phase 1: Database Setup
1. **Create a Migration for the To-Do Table**
   - Create a new migration file to add a `todo_tasks` table with the following fields:
     - `id` (serial, primary key)
     - `team_id` (foreign key to teams)
     - `title` (varchar(255))
     - `description` (text, nullable)
     - `status` (varchar(20), default 'pending')
     - `created_by` (foreign key to users)
     - `created_at` (timestamp, default now())
     - `updated_at` (timestamp, default now())
   - Run the migration to ensure the table is created successfully.

2. **Update the Database Schema**
   - Update the existing schema file to include the new `TodoTask` type and its relations to the `Team` and `User` types.
   - Ensure that the necessary type exports are included.

## Phase 2: Backend API Setup
3. **Add Database Queries**
   - Implement the following database query functions in `lib/db/queries.ts`:
     - `createTodoTask`: To create a new to-do task.
     - `getTodoTasksForTeam`: To retrieve all to-do tasks for a specific team.
     - `updateTodoTask`: To update a specific to-do task.
     - `deleteTodoTask`: To delete a specific to-do task.
   - Test each query function individually to ensure they work as expected.

4. **Update Activity Logging**
   - Update the `ActivityType` enum in `schema.ts` to include:
     - `CREATE_TODO`
     - `UPDATE_TODO`
     - `DELETE_TODO`
   - Ensure that activity logging is implemented for these actions.

## Phase 3: Frontend - Task List View
5. **Create Task List UI**
   - Add a new "Tasks" section in the dashboard.
   - Create a table or list view component to display the to-do tasks.
   - Implement loading and empty states for the task list.

6. **Implement Task Fetching**
   - Add server-side data fetching to retrieve the list of to-do tasks for the user's team.
   - Display the tasks in the UI and handle any errors that may occur during fetching.

## Phase 4: Frontend - Task Creation
7. **Create "New Task" Functionality**
   - Create a form component for adding new tasks, including validation.
   - Implement the action to create a new task using the `createTodoTask` function.
   - Add success and error states to provide feedback to the user.
   - Ensure that the form is only visible to users with the owner role.

## Phase 5: Frontend - Task Management
8. **Implement Task Updates**
   - Add edit functionality to the task list, allowing users to update existing tasks.
   - Create an update form or modal for editing tasks, including validation.
   - Ensure that both owners and members can update tasks.

9. **Implement Task Deletion**
   - Add a delete confirmation dialog for tasks.
   - Implement the action to delete a task using the `deleteTodoTask` function.
   - Provide success and error feedback to the user.
   - Ensure that both owners and members can delete tasks.

## Phase 6: Access Control
10. **Implement Role-Based Access Control**
    - Modify UI components to show/hide features based on user roles (owner vs. member).
    - Add server-side validation to ensure that only authorized users can perform certain actions.
    - Test all operations with different user roles to confirm proper access control.

## Phase 7: Testing & Refinement
11. **Test the Complete Flow**
    - Verify that all CRUD operations (Create, Read, Update, Delete) work as expected.
    - Test role-based access to ensure that permissions are enforced correctly.
    - Check activity logging to confirm that actions are recorded properly.
    - Verify error handling for all operations.

Once you confirm that each step works as expected, we can proceed to the next step. Would you like to start with Phase 1 and create the migration for the To-Do table?
