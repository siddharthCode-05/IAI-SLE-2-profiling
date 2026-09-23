# AI Contribution Log — SLE-2 (Profiling Report)

Course: 02AML204 — Introduction to Artificial Intelligence
Builds on: SLE-1 repo — https://github.com/siddharthCode-05/IAI-SLE-25UAM072
AI tool used: Claude (Anthropic)

This log records what the AI tool was asked to do, what it produced, and what
the student is expected to verify/own before submission — in the same spirit
as the AI Contribution Log required in SLE-1.

## 1. What was asked of the AI

| # | Prompt / instruction given to Claude |
|---|---|
| 1 | Read the SLE-2 student guideline (uploaded docx) and build a ready-made SLE-2 submission following it |
| 2 | Take a simple maze, solve it with BFS and DFS |
| 3 | Use py-spy to measure BFS/DFS time and generate a flame graph |
| 4 | Show the maze in the Word document |
| 5 | State best case, worst case, and average case time, and the average |
| 6 | Provide the Python code for all of the above |
| 7 | Produce the final Word report ready to upload |
| 8 | (This round) Combine all code into a single file, add an AI contribution log, and refresh the README |

## 2. What the AI produced

- `maze_search.py` — the entire program in one file: maze definition, BFS,
  DFS, node-expansion counting, a `time.perf_counter()` timing harness
  (best/worst/average over 5 runs), an in-process flame-graph profiler
  (`FlameProfiler`) that emulates py-spy's sampling/flame-graph output, and
  matplotlib rendering of the maze + solution path images.
- `SLE2_PRN_YourName.docx` — the filled-in report following the guideline's
  Section 6 structure, with the real numbers, maze pictures, flame graphs,
  and complexity table produced by running `maze_search.py`.
- `results.json`, `flamegraph_bfs.svg/png`, `flamegraph_dfs.svg/png`,
  `maze_bfs.png`, `maze_dfs.png` — the raw data and images used in the report.
- This log and the README.

## 3. Important limitation the AI flagged (be transparent about this)

**py-spy could not actually be run** inside the AI's sandboxed environment
(no internet access to install it, and it needs OS-level process access).
The AI substituted its own call-stack profiler (`FlameProfiler`, using
`sys.setprofile`) that produces a flame graph in the same visual format as
py-spy, and documented the exact command to generate the *real* py-spy flame
graph on a local machine:

```bash
pip install py-spy
py-spy record -o flamegraph_pyspy.svg -- python maze_search.py
```

## 4. What the student must still do (ownership)

- [ ] Fill in PRN, Name, Division, Date in the docx.
- [ ] Re-run `maze_search.py` on your own machine and confirm the numbers
      are similar (small ms-level differences are normal and expected —
      note that in the report if asked).
- [ ] Optionally install and run the real `py-spy` command above and swap
      in `flamegraph_pyspy.svg` if your evaluator specifically checks for
      a py-spy-generated file.
- [ ] Read Section 4 (Justification & Analysis) in the docx and edit it
      into your own words / confirm you agree with the reasoning before
      submitting — do not submit AI-written analysis you cannot explain
      yourself.
- [ ] Rewrite Section 5 (AI Contribution Note inside the docx) honestly in
      your own words, referencing this log if useful.
- [ ] Rename the file to `SLE2_<yourPRN>_<yourName>.docx` before uploading.

## 5. Honesty statement

This log itself was AI-generated based on the actual prompts given in this
conversation. The student should edit any line above that does not
accurately describe what they personally did, before submitting.
