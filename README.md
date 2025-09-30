# ===== ROMA: Ready-to-Run Example =====

# Check if a task is atomic (simple)
def is_atomic(task):
    # For this example, a task is atomic if it is a single word
    return isinstance(task, str) and len(task.split()) == 1

# Execute an atomic task
def execute(task):
    # Dummy execution: just return a string indicating the task was executed
    return f"Executed: {task}"

# Plan function: split complex tasks into subtasks
def plan(task):
    # For this example, split by words
    return task.split()

# Aggregate results from subtasks
def aggregate(results):
    # Join all results into a single string
    return " | ".join(results)

# Recursive solver
def solve(task):
    if is_atomic(task):
        # Atomic task → execute directly
        return execute(task)
    else:
        # Complex task → split into subtasks
        subtasks = plan(task)
        results = []
        for subtask in subtasks:
            results.append(solve(subtask))  # Recursive call
        return aggregate(results)

# ===== Example Usage =====
if __name__ == "__main__":
    initial_request = "Learn about ROMA"
    answer = solve(initial_request)
    print("Final result:", answer)
