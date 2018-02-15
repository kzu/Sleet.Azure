# Sleet.Azure

Provides the Sleet.Azure package for easily pushing packages to Azure storage-backed feeds

# Installing

See https://www.nuget.org/packages/Sleet.Azure

# Usage

You must provide the following three required properties:

```xml
    <!-- Azure storage account to use -->
    <StorageAccount Condition="'$(StorageAccount)' == ''" />
    <!-- Azure storage access key for the connection -->
    <StorageAccessKey Condition="'$(StorageAccessKey)' == ''" />
    <!-- Azure storage container name where the feed will be stored -->
    <StorageContainer Condition="'$(StorageContainer)' == ''" />
```

and optionally:

```xml
    <!-- 
      Whether to validate and initialize the feed before pushing. 
      Defaults to 'true', which is expensive and can safely be 
      turned to 'false' after the first init/push operation.
     -->
    <SleetInit>true</SleetInit>
```

You specify the packages to push via the `Package` item group:

```xml
<ItemGroup>
    <Package Include="bin\*.nupkg" />
</ItemGroup>
```

And then invoke the `Push` target. Optionally, invoke `Init` the 
first time you initialize the feed.

