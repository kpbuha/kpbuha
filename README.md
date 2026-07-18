<div align="center">

### `man kpbuha`

<sub>**KPBUHA(1)** · General Commands Manual · **KPBUHA(1)**</sub>

</div>

---

### NAME

**kpbuha** — systems engineer; writes C++ that shares memory without regret

### SYNOPSIS

```console
kpbuha [--lang c++20] [--domain systems|security] [-j $(nproc)] [--sanitize=thread]
```

### DESCRIPTION

Software engineer working in **modern C++** on systems-level code, currently in
cloud security. Spends most of the day somewhere between a thread and the thing
it was supposed to be protecting.

Believes a thing is only understood once you can rebuild it from scratch — which
is why the side projects are all *"write your own X"*: a shell, a thread pool, an
allocator, a lock-free queue.

```cpp
namespace kpbuha {

// A thing is understood only when it can be rebuilt from scratch.
template <class T>
concept Understood = requires(T t) {
    { t.build_from_scratch() } -> std::same_as<T>;
    { t.explain() }           -> std::convertible_to<std::string_view>;
};

class Engineer {
public:
    static constexpr std::string_view lang  = "C++20";
    static constexpr std::string_view focus = "concurrency · systems · security";

    [[noreturn]] void loop() {
        while (true) {
            read(); build(); break_it(); fix_it(); understand();
        }
    }
};

}  // namespace kpbuha

static_assert(Understood<Shell>);   // built one. coroutines and all.
```

### CURRENTLY RUNNING

| PID | STAT | COMMAND |
|----:|:----:|:--------|
| 1 | `R` | **SHeLL** — a POSIX shell in C++20: coroutine execution engine, job control, signals, termios handoff |
| 2 | `R` | **mt-mastery** — working up from `std::thread` to lock-free MPMC queues and work-stealing pools |
| 3 | `S` | **DSA** — 1,000+ problems deep, still blocked on `segment_tree` |
| 4 | `Z` | that side project from 2021 <sub>(defunct, will not be reaped)</sub> |

### ENVIRONMENT

```ini
LANGUAGES = C++20, C, Python, a little JavaScript from a past life
CONCURRENCY = std::thread, condition_variable, atomics, memory_order, coroutines
TOOLING = CMake, gdb, ThreadSanitizer, Helgrind, perf, git
SYSTEMS = POSIX, signals, process groups, sockets, memory models
```

### DIAGNOSTICS

```
$ ./build/bathroom_problem
ThreadSanitizer: reported 0 warnings
```

<sub>It took four rewrites and one very real deadlock to earn that line. The first
fairness fix introduced a circular wait — both groups waiting on a counter only
the other could decrement. Fairness bugs are just deadlocks with good intentions.</sub>

### EXIT STATUS

Returns `0` on success. Has never once returned `0` on the first run.

### SEE ALSO

**leetcode**(1) — [`kpbuha`](https://leetcode.com/u/kpbuha/) · **email**(1) — [`karanbuha0@gmail.com`](mailto:karanbuha0@gmail.com)

---

<div align="center">
<sub>Most of the interesting repositories are private. Ask.</sub>
</div>
