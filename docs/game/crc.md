# Crc

The game is using a modified FNV32-a alrogithm to calculate Crc values from strings
and uses them for identification for most of the static assets and ingame stuff.

As the FNV32 is a hashing alrogithm, we are unable to get the original string back
from the hash, but bruteforcing and targeted guessing can be used to find more values.

This hash implementation is case-insensitive, so the hashes of "TEST"
and "test" are the same.

C# algorithm:

```csharp
public const uint FNV32Offset = 0x811C9DC5u;
public const uint FNV32Prime = 0x1000193u;

public static uint FNV32string(string source, int maxLen = -1)
{
    if (string.IsNullOrEmpty(source))
        return 0;

    var bytes = Encoding.UTF8.GetBytes(source);
    var hash = FNV32Offset;

    for (var i = 0; i < bytes.Length && (maxLen == -1 || i < maxLen); ++i)
        hash = FNV32Prime * (hash ^ (bytes[i] | 0x20u));
    
    return (hash ^ 0x2Au) * FNV32Prime;
}
```

The [SabTool](../tools/sabtool.md#SabTool) tool can calculate, bruteforce and look
up hashes (from a hash to string lookup file, that was manually created
for this purpose).
