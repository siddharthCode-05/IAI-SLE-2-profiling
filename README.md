# SLE-2: Profiling Report — BFS vs DFS on a Maze

Course: 02AML204 — Introduction to Artificial Intelligence
Builds on: SLE-1 repo — https://github.com/siddharthCode-05/IAI-SLE-25UAM072

## What's here

| File | Purpose |
|---|---|
| `maze_search.py` | **Everything in one file** — maze, BFS, DFS, timing harness, flame-graph profiler, and maze/flame-graph image rendering |
| `AI_CONTRIBUTION_LOG.md` | Log of what the AI tool (Claude) was asked to do and produced, and what you must still verify/own |
| `SLE2_PRN_YourName.docx` | The final report — **rename this to `SLE2_<yourPRN>_<yourName>.docx` before uploading to Moodle** |
| `results.json` | Raw timing/node numbers produced by `maze_search.py` |
| `flamegraph_bfs.svg` / `.png`, `flamegraph_dfs.svg` / `.png` | Flame graphs (py-spy-style visualization) |
| `maze_bfs.png`, `maze_dfs.png` | Maze + solution path pictures used in the report |

## How to run it — one command, one file

```bash
pip install matplotlib   # only external dependency (for the maze images)
python maze_search.py
```

This single run prints the BFS/DFS solved mazes and the timing table to the
console, and writes all of these to the same folder:

```
flamegraph_bfs.svg / flamegraph_bfs.png
flamegraph_dfs.svg / flamegraph_dfs.png
maze_bfs.png / maze_dfs.png
results.json
```

(PNG conversion of the flame graphs uses LibreOffice/`soffice` if it's
installed on your machine; if not, the `.svg` files still open fine in any
browser.)

## Reproducing the *official* py-spy flame graph

`maze_search.py` includes its own in-process flame-graph profiler
(`FlameProfiler`) so it works even without py-spy installed. To generate the
actual py-spy flame graph the guideline recommends, run this separately
(needs internet access to `pip install`, and OS-level process permissions):

```bash
pip install py-spy
py-spy record -o flamegraph_pyspy.svg -- python maze_search.py
```

## Before you submit

1. Read `AI_CONTRIBUTION_LOG.md` — it lists exactly what the AI did and a
   checklist of what you still need to verify/do yourself.
2. Open `SLE2_PRN_YourName.docx`, fill in your **PRN**, **Name**, **Division**, **Date**.
3. Rewrite Section 5 (AI Contribution Note) in the docx in your own words.
4. Re-run `maze_search.py` on your own machine if you want your own measured
   numbers instead of the ones already filled in.
5. Rename the file to `SLE2_<PRN>_<YourName>.docx` and upload to Moodle.
