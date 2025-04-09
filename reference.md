---
icon: code
order: 95
---

# Reference

=== Scheduler
Provides methods to schedule and manage tasks. It supports both synchronous and asynchronous task execution with various timing options.

```lua
--- Schedules a task to run on the next tick.
--  @param handler The task function to execute
scheduler:run(handler: () -> void): BukkitTask

--- Schedules an asynchronous task to run on the next tick.
--  @param handler The task function to execute
scheduler:runAsync(handler: () -> void): BukkitTask

--- Schedules a task to run after a delay (in ticks).
--  @param handler The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runLater(handler: () -> void, delay: number): BukkitTask

--- Schedules an asynchronous task to run after a delay (in ticks).
--  @param handler The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runLaterAsync(handler: () -> void, delay: number): BukkitTask

--- Schedules a repeating task.
--  @param handler The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeating(handler: () -> void, delay: number, period: number): BukkitTask

--- Schedules an asynchronous repeating task.
--  @param handler The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeatingAsync(handler: () -> void, delay: number, period: number): BukkitTask

--- Cancels a task with the specified identifier.
--  @param task The task to cancel
scheduler:cancel(task: number): void
```