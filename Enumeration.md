

Enumerate all folders where we have write access. Launch on C:\
```powershell
 $userProfile = $env:USERPROFILE; Get-ChildItem -Recurse -Directory -ErrorAction SilentlyContinue | Where-Object { $_.FullName -notlike "$userProfile\*" } | ForEach-Object { $testFile = "$($_.FullName)\testfile.tmp"; try { New-Item -Path $testFile -ItemType File -Force -ErrorAction Stop | Out-Null; Remove-Item -Path $testFile -Force; $_.FullName } catch { } }
```

text

```powershell

```
