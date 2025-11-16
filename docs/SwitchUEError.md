[DevMemo](../index.md)

# `Switch Unreal Engine version`でJsonパースエラーが発生した場合の対応

下記のようなエラーが発生する

```
  at EpicGames.Core.JsonObject.ParseUtf8File(String path)
   at EpicGames.Core.JsonObject.Read(FileReference file)
   at UnrealBuildTool.PluginDescriptor.FromFile(FileReference FileName)Wrapped by JsonException: '0xFF' is an invalid start of a value. LineNumber: 0 | BytePositionInLine: 0. (in path/to/yourplugin.uplugin)
   at UnrealBuildBase.Parallel2.ForEach[TSource](IEnumerable`1 source, Action`1 body, Int32 helperCount, Boolean useTasks)
   at UnrealBuildTool.ProjectFileGenerator.AddProjectsForAllTargets(PlatformProjectGeneratorCollection PlatformProjectGenerators, List`1 AllGames, List`1 AllTargetFiles, String[] Arguments, List`1 EngineProjects, List`1 GameProjects, Dictionary`2 ProjectFileToUProjectFile, Dictionary`2 ProgramProjects, Dictionary`2 RulesAssemblies, ILogger Logger)
   at UnrealBuildTool.ProjectFileGenerator.GenerateProjectFiles(PlatformProjectGeneratorCollection PlatformProjectGenerators, String[] Arguments, ILogger Logger)
   at UnrealBuildTool.GenerateProjectFilesMode.ExecuteAsync(CommandLineArguments Arguments, ILogger Logger)
   at UnrealBuildTool.UnrealBuildTool.Main(String[] ArgumentsArray)

Result: Failed (OtherCompilationError)
Total execution time: 0.83 seconds
```

.uplugin が壊れているので別プロジェクトで新規プラグインを作成 → Modulesなど必要な情報を追記 → エラーが出ているファイルに上書き で解消できる