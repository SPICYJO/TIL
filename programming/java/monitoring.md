# Monitoring Java processes

## Check Java process's pid

<details>
    <summary>jps command</summary>

```bash
jps [-m][-v]
```

- Java Virtual Machine Process Status Tool
- jps is located at `%JAVA_HOME%/bin`

</details>

## Thread Dump and Heap Dump

<details>
    <summary>thread dump</summary>

```bash
jstack <PID>
jstack <PID> > filename.txt
```

- Stack Trace
- jstack is located at `%JAVA_HOME%/bin`

</details>

<details>
    <summary>heap dump</summary>

```bash
jmap -dump:format=b,file=<filename> <PID>
```

- Memory Map
- jmap is located at `%JAVA_HOME%/bin`

</details>

<details>
    <summary>dump analysis tool</summary>

- VisualVM
- IntelliJ IDEA supports analysis (available in Ultimate edition)
- Web analysis tool: https://fastthread.io/

</details>