# NuGet Package Generation

This guide explains two common ways to generate a NuGet package from a C# project.

---

## Method 1: Using `nuget` CLI

This method is ideal for **older projects** (e.g., .NET Framework or non-SDK-style projects).

### Steps:
1. Open a terminal and navigate to the project folder.
2. Run the following command to generate a `.nuspec` file:
   ```bash
   nuget spec
   ```
   This creates a `<project-name>.nuspec` file with placeholder metadata.

3. Open the `.nuspec` file and fill in the required metadata:
   - `id`
   - `version`
   - `authors`
   - `description`
   - etc.

4. Generate the `.nupkg` package:
   ```bash
   nuget pack <project-name>.csproj
   ```
   This builds the project and uses the `.nuspec` file to generate the package in the current directory.

> You can also pack using the `.nuspec` directly:
```bash
nuget pack <project-name>.nuspec
```

---

## Method 2: Using `dotnet` CLI

Use this method for **modern SDK-style projects** (.NET Core / .NET 5+).

### Steps:
1. Open a terminal and navigate to the project folder.
2. Run the following command:
   ```bash
   dotnet pack
   ```
   This uses the metadata defined in the `.csproj` file and builds the `.nupkg` package.

### Optional Flags:
- To specify the output directory:
  ```bash
  dotnet pack -o ./nupkgs
  ```
- To include symbols:
  ```bash
  dotnet pack --include-symbols
  ```

> No `.nuspec` file is needed; all metadata should be in the `.csproj`.

---

## Notes

- Use `dotnet` CLI for newer projects that follow the SDK-style format.
- Use `nuget` CLI if you're working with older, non-SDK-style projects.
- Both methods support pushing the package to NuGet:
  - `nuget push <package>.nupkg -Source <source-url> -ApiKey <key>`
  - `dotnet nuget push <package>.nupkg --source <source-url> --api-key <key>`

---

## References

- [NuGet CLI Reference](https://learn.microsoft.com/nuget/reference/nuget-exe-cli-reference)
- [dotnet pack Documentation](https://learn.microsoft.com/dotnet/core/tools/dotnet-pack)
