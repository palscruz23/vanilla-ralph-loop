# Focus Flow Web MVP Task Breakdown

## 0. Setup
- [ ] Create a small web app scaffold.
- [ ] Set up folders for `src`, `components`, `pages`, `styles`, `lib`, and `tests`.
- [ ] Add one main layout and one home page.

## 1. Task Data
- [ ] Create a simple task model with title, status, and optional due date.
- [ ] Add local persistence for tasks.
- [ ] Add a small data layer that keeps storage logic out of UI components.

## 2. Add Task Flow
- [ ] Build a simple form to add a task.
- [ ] Let the user enter a title and optional due date.
- [ ] Validate that the title is not empty.

## 3. Task List
- [ ] Show saved tasks in a list.
- [ ] Show an empty state when no tasks exist.
- [ ] Allow marking a task as done.
- [ ] Allow deleting a task.

## 4. Filters
- [ ] Add filters for all, active, and completed tasks.
- [ ] Show the correct task count for the current filter.
- [ ] Keep filter behavior simple and easy to verify.

## 5. Quality
- [ ] Add tests for add, complete, delete, and filter behavior.
- [ ] Run the project build.
- [ ] Run the test suite.

## Definition of Done
- [ ] User can add, complete, filter, and delete tasks.
- [ ] Data stays available after refresh.
- [ ] Build and tests pass.
