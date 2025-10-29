# Blueprint 変数・関数のデフォルトアクセス指定子を`private`にする

Engine\Source\Editor\UnrealEd\Private\Kismet2\BlueprintEditorUtils.cpp
4721行目あたり
``` C++
FBlueprintEditorUtils::AddMemberVariable(UBlueprint* Blueprint, const FName
		NewVar.SetMetaData(TEXT("MultiLine"), TEXT("true"));
	}

	NewVar.SetMetaData(FBlueprintMetadata::MD_Private, "true");    // 変数の初期アクセス権をPrivateに
	Blueprint->NewVariables.Add(NewVar);

	// Potentially adjust variable names for any child blueprints

```

Engine\Source\Editor\UnrealEd\Public\Kismet2\BlueprintEditorUtils.h
356行目あたり
``` C++
			if ( bIsUserCreated )
			{
				// We need to flag the entry node to make sure that the compiled function is callable from Kismet2
				int32 ExtraFunctionFlags = ( FUNC_BlueprintCallable | FUNC_BlueprintEvent | FUNC_Private ); // 関数の初期アクセス権をPrivateに
				if ( Blueprint->BlueprintType == BPTYPE_Interface )
				{
					// Interface の場合はpublicにする必要がある
					ExtraFunctionFlags = (FUNC_BlueprintCallable | FUNC_BlueprintEvent | FUNC_Public);
				}

				if ( BPTYPE_FunctionLibrary == Blueprint->BlueprintType )
				{
					ExtraFunctionFlags |= FUNC_Static;

```