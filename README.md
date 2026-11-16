# CodeForFun

Small fun programs, written just for laughs.

## Funny Propose

A joke Windows program: a tiny Win32 C++ app that pops up a window titled
"Will You Marry Me?"

- Click **Yes** and it thanks you for accepting.
- Click **No** and it keeps asking "Are you sure?" — it only gives up after a
  lot of refusals.

The source is the file `Funny Propose` (C++ source; the file has no extension).

### Build (Windows)

With MinGW:

```bat
g++ "Funny Propose" -o FunnyPropose.exe -mwindows
```

Or open it in Visual Studio as a Win32 application and build it there.

Run `FunnyPropose.exe` and try saying no.

## License

MIT — see [LICENSE](LICENSE).
