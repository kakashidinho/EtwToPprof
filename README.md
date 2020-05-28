# EtwToPprof

EtwToPprof exports ETW traces to pprof protobuf format. It uses the [.NET
TraceProcessing
API](https://www.nuget.org/packages/Microsoft.Windows.EventTracing.Processing.All)
to process ETW traces.

This tool was built for processing ETW traces from Chrome, so the default values
of the flags are based on that use case. It uses _NT_SYMCACHE_PATH and _NT_SYMBOL_PATH for
symbolizing traces if set, otherwise it uses WPA defaults.

## Building:

Build the provided Visual Studio Solution with VS 2019.

### Nuget dependencies (included in solution):
- CommandLineParser v2.8.0
- Google.Protobuf v3.11.4
- Microsoft.Windows.EventTracing.Processing.All v1.0.0

## Command line flags:

  -o, --outputFileName            (Default: profile.pb.gz) Output file name for gzipped pprof profile.

  -p, --processFilter             (Default: chrome.exe,dwm.exe,audiodg.exe) Filter for process name to be included in the exported profile. All processes will be exported if empty.

  --includeInlinedFunctions       (Default: false) Whether inlined functions should be included in the exported profile (slow).

  --stripSourceFileNamePrefix     (Default: ^c:/b/s/w/ir/cache/builder/) Prefix regex to strip out of source file names in the exported profile.

  --timeStart                     Start of time range to export in seconds

  --timeEnd                       End of time range to export in seconds

  --includeProcessAndThreadIds    (Default: false) Whether process and thread ids are included in the exported profile.

  --help                          Display this help screen.

  --version                       Display version information.

  etlFileName (pos. 0)            Required. ETL trace file name.

## Disclaimer:

**This is not an officially supported Google product.**
