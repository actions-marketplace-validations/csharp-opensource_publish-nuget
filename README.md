# Example

```yml
name: Nuget Package
on:
  release:
    types: [published]

jobs:
  build:
    runs-on: ubuntu-20.04
    name: Update NuGet package
    steps:
      - name: Checkout repository
        uses: actions/checkout@v1

      - name: Setup .Net
        uses: actions/setup-dotnet@v1

      - name: Nuget Package And Upload
        uses: csharp-extensions/publish-nuget@v1
        with:
          releaseVersion: ${{ github.event.release.tag_name }}
          repoUrl: ${{ github.server_url }}/${{ github.repository }}
          nugetToken: ${{secrets.NUGET_AUTH_TOKEN}}
          nugetSource: https://api.nuget.org/v3/index.json
```
