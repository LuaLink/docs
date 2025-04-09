---
icon: code
order: 96
---

# Reference

=== Scheduler
Provides methods to schedule and manage tasks. It supports both synchronous and asynchronous task execution with various timing options.

```lua
--- Schedules a task to run on the next tick.
--  @param callback The task function to execute
scheduler:run(callback: () -> void): void

--- Schedules an asynchronous task to run on the next tick.
--  @param callback The task function to execute
scheduler:runAsync(callback: () -> void): void

--- Schedules a task to run after a delay (in ticks).
--  @param callback The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runDelayed(callback: (task: BukkitTask) -> void, delay: number): BukkitTask

--- Schedules an asynchronous task to run after a delay (in ticks).
--  @param callback The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runDelayedAsync(callback: (task: BukkitTask) -> void, delay: number): BukkitTask

--- Schedules a repeating task.
--  @param callback The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeating(callback: (task: BukkitTask) -> void, delay: number, period: number): BukkitTask

--- Schedules an asynchronous repeating task.
--  @param callback The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeatingAsync(callback: (task: BukkitTask) -> void, delay: number, period: number): BukkitTask
```