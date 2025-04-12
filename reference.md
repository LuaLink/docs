---
icon: code
order: 95
---

# Reference

=== Script
Main script class available in the global scope of each script. Provides access to various utilities.
```lua Variables
--- Returns the name of the script.
script.name: string

--- Returns the script's Logger instance.
script.logger: Logger
```
```lua Functions
--- Registers a server command that players and console can execute.
--  @param handler The command handler function
--  @param metadata The command metadata table
script:registerCommand(handler: (sender: CommandSender, args: table) -> void, metadata: table): void

--- Registers an event listener.
--  @param event The event class
--  @param handler The event handler function
script:registerListener(event: string, handler: (event: Event) -> void): void
```

=== Scheduler
Provides methods to schedule and manage tasks. It supports both synchronous and asynchronous task execution with various timing options.

```lua Functions
--- Schedules a task to run on the next tick.
--  @param handler The task function to execute
scheduler:run(handler: (BukkitRunnable) -> void): BukkitTask

--- Schedules an asynchronous task to run on the next tick.
--  @param handler The task function to execute
scheduler:runAsync(handler: (BukkitRunnable) -> void): BukkitTask

--- Schedules a task to run after a delay (in ticks).
--  @param handler The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runDelayed(handler: (BukkitRunnable) -> void, delay: number): BukkitTask

--- Schedules an asynchronous task to run after a delay (in ticks).
--  @param handler The task function to execute
--  @param delay Delay in ticks before execution
scheduler:runDelayedAsync(handler: (BukkitRunnable) -> void, delay: number): BukkitTask

--- Schedules a repeating task.
--  @param handler The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeating(handler: (BukkitRunnable) -> void, delay: number, period: number): BukkitTask

--- Schedules an asynchronous repeating task.
--  @param handler The task function to execute
--  @param delay Delay in ticks before first execution
--  @param period Interval in ticks between executions
scheduler:runRepeatingAsync(handler: (BukkitRunnable) -> void, delay: number, period: number): BukkitTask

--- Cancels a task with the specified identifier.
--  @param task The task to cancel
scheduler:cancel(task: number | runnable: BukkitRunnable | task: BukkitTask): void
```
