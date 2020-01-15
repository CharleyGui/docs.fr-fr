---
title: Migration C++de projets/CLI vers .net Core
description: En savoir plus sur C++le portage de projets/CLI vers .net core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964929"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Guide pratique pour porter C++un projet/CLI vers .net Core

À compter de .net Core 3,1 et de Visual Studio 2019 version 16,4, [ C++les projets/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) peuvent cibler .net core. Cette prise en charge permet de porter les applications de bureau C++Windows avec des couches Interop/CLI vers .net core. Cet article explique comment déplacer C++des projets/cli de .NET Framework vers .net Core 3,1.

## <a name="ccli-net-core-limitations"></a>C++Limitations de .NET Core/CLI

Il existe quelques limitations importantes pour le portage C++de projets/CLI vers .net Core par rapport à d’autres langages :

* C++La prise en charge de .NET Core/CLI est Windows uniquement.
* C++Les projets/CLI ne peuvent pas cibler .NET Standard, mais uniquement .NET Core (ou .NET Framework).
* C++Les projets/CLI ne prennent pas en charge le nouveau format de fichier de projet de type SDK. Au lieu de cela, même quand vous C++ciblez .net Core, les projets/CLI utilisent le format de fichier vcxproj existant.
* C++Les projets/CLI ne peuvent pas multicibler plusieurs plateformes .NET. Si vous avez besoin de générer C++un projet/cli pour .NET Framework et .net Core, utilisez des fichiers de projet distincts.
* .NET Core ne prend pas en charge la compilation `-clr:pure` ou `-clr:safe`, mais uniquement la nouvelle option `-clr:netcore` (qui est équivalente à `-clr` pour .NET Framework).

## <a name="port-a-ccli-project"></a>Porter un C++projet/CLI

Pour porter un C++projet/CLI vers .net Core, apportez les modifications suivantes au fichier vcxproj. Ces étapes de migration diffèrent des étapes requises pour les autres types C++de projets, car les projets/CLI n’utilisent pas de fichiers projet de type SDK.

1. Remplacez `<CLRSupport>true</CLRSupport>` propriétés par `<CLRSupport>NetCore</CLRSupport>`. Cette propriété est souvent dans des groupes de propriétés spécifiques à la configuration. vous devrez donc peut-être la remplacer à plusieurs emplacements.
2. Remplacez `<TargetFrameworkVersion>` propriétés par `<TargetFramework>netcoreapp3.1</TargetFramework>`.
3. Supprimez toutes les références .NET Framework (par exemple `<Reference Include="System" />`). Les assemblys kit SDK .NET Core sont automatiquement référencés lors de l’utilisation de `<CLRSupport>NetCore</CLRSupport>`.
4. Mettez à jour l’utilisation des API dans les fichiers CPP, si nécessaire, pour supprimer les API non disponibles pour .NET Core. Étant C++donné que les projets/CLI ont tendance à être des couches d’interopérabilité assez étroites, il n’y a souvent pas beaucoup de modifications nécessaires. L' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) peut être utilisé pour identifier les API .net non prises en C++charge utilisées par les fichiers binaires/CLI, tout comme avec les fichiers binaires purement managés. Les instructions relatives à la détermination de la portabilité du code et à la mise à jour des projets à utiliser avec les API .NET Core sont disponibles dans le [Guide de portage des bibliothèques](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>Utilisation de WPF et de Windows Forms

Les projets C++.net Core/CLI peuvent utiliser des API Windows Forms et WPF. Pour utiliser ces API de bureau Windows, vous devez ajouter des références d’infrastructure explicites aux bibliothèques de l’interface utilisateur. Les projets de type SDK qui utilisent les API de bureau Windows référencent automatiquement les bibliothèques d’infrastructure nécessaires à l’aide du kit de développement logiciel (SDK) `Microsoft.NET.Sdk.WindowsDesktop`. Étant C++donné que les projets/CLI n’utilisent pas le format de projet de type SDK, ils doivent ajouter des références d’infrastructure explicites lors du ciblage de .net core.

Pour utiliser des API Windows Forms, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Pour utiliser les API WPF, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Pour utiliser les Windows Forms et les API WPF, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Actuellement, il n’est pas possible d’ajouter ces références à l’aide du gestionnaire de références de Visual Studio. À la place, mettez à jour le fichier projet manuellement. Cette mise à jour peut être effectuée dans Visual Studio en déchargeant le projet, puis en modifiant le fichier projet. Vous pouvez également utiliser un autre éditeur comme VS Code.

## <a name="build-without-msbuild"></a>Générer sans MSBuild

Il est également possible de générer C++des projets/CLI sans utiliser MSBuild. Procédez comme suit pour générer C++un projet/CLI pour .net Core directement avec *CL. exe* et *Link. exe*:

1. Lors de la compilation, passer `-clr:netcore` à *CL. exe*.
2. Référencez les assemblys de référence .NET Core nécessaires.
3. Lors de la liaison, fournissez le répertoire hôte de l’application .NET Core en tant que `LibPath` (afin que *ijwhost. lib* puisse être trouvé).
4. Copiez *ijwhost. dll* (à partir du répertoire hôte de l’application .net Core) dans le répertoire de sortie du projet.
5. Assurez-vous qu’il existe un fichier [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) pour le premier composant de l’application qui exécutera le code managé. Si l’application a un point d’entrée géré, un fichier de `runtime.config` est créé et copié automatiquement. Toutefois, si l’application a un point d’entrée natif, vous devez créer un fichier `runtimeconfig.json` pour la première C++bibliothèque/CLI afin d’utiliser le Runtime .net core.

## <a name="known-issues"></a>Problèmes connus

Il existe quelques problèmes connus à prendre en compte lors de l’utilisation C++de projets/CLI ciblant .net core.

* Une référence d’infrastructure WPF dans les C++projets .net Core/CLI provoque actuellement des avertissements superflus concernant l’impossibilité d’importer des symboles. Ces avertissements peuvent être ignorés sans risque et doivent être corrigés prochainement.
* Si l’application dispose d’un point d’entrée natif C++, la bibliothèque/CLI qui exécute en premier le code managé a besoin d’un fichier [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) . Ce fichier de configuration est utilisé lors du démarrage du Runtime .NET Core. C++Les projets/CLI ne créent pas encore `runtimeconfig.json` fichiers automatiquement au moment de la génération, le fichier doit donc être généré manuellement. Si une C++bibliothèque/CLI est appelée à partir d’un point d’entrée managé C++, la bibliothèque/CLI n’a pas besoin d’un fichier `runtimeconfig.json` (car l’assembly de point d’entrée en aura un qui est utilisé lors du démarrage du Runtime). Un exemple simple de `runtimeconfig.json` fichier est présenté ci-dessous. Pour plus d’informations, consultez la [spécification sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
