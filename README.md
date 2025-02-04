# Inconsistent Iteration Order with Lua's 'pairs' Iterator

This repository demonstrates a potential issue with Lua's `pairs` iterator: its iteration order isn't guaranteed to be consistent across different Lua versions or implementations.  This can lead to unexpected behavior, especially in scenarios involving recursion or when the order of elements matters.

## The Problem

The `pairs` function is used to iterate over the key-value pairs of a table.  While it works correctly, the order in which it iterates isn't formally specified, meaning that the order may differ depending on the Lua version or environment. This can cause problems in recursive functions or other situations where the iteration order is implicitly relied upon.

## Reproducing the Issue

The `bug.lua` file contains a simple example that highlights this potential inconsistency.  Run the script with different Lua interpreters (e.g., LuaJIT, standard Lua) to potentially observe differing output. The output may not always be in the same order as one would expect based on the table structure.

## Solution

The `bugSolution.lua` offers a potential mitigation if strict iteration order is critical.  This solution uses an alternative approach to iteration, ensuring that the elements are processed in a predictable order. However, keep in mind that using this solution might impact performance due to increased complexity in the iteration.

## Note

While this isn't a 'bug' in the strictest sense (it's documented behavior), it's crucial to be aware of this potential inconsistency to avoid subtle and hard-to-debug issues in your Lua programs. It is recommended to avoid relying on the order of elements in tables when iterating with `pairs` unless you explicitly have a specific need for the default ordering provided by your implementation.