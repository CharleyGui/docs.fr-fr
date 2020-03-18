---
title: Migrer les projets CMD/CLI à .NET Core
description: En savoir plus sur le portage des projets CMD/CLI à .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964929"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Comment porter un projet CMD/CLI à .NET Core

À partir de .NET Core 3.1 et Visual Studio 2019 version 16.4, [les projets C'/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) peuvent cibler .NET Core. Ce support permet de porter des applications de bureau Windows avec des couches interop C'/CLI à .NET Core. Cet article décrit comment portuairer les projets CMD/CLI du cadre .NET au .NET Core 3.1.

## <a name="ccli-net-core-limitations"></a>Limitations de base CMD/CLI .NET

Il y a quelques limites importantes au portage des projets de C/CLI à .NET Core par rapport à d’autres langues :

* La prise en charge de C/CLI pour .NET Core est Uniquement Windows.
* Les projets C/CLI ne peuvent pas cibler .NET Standard, seulement .NET Core (ou .NET Framework).
* Les projets CMD/CLI ne prennent pas en charge le nouveau format de fichier de projet de type SDK. Au lieu de cela, même lorsque vous ciblez .NET Core, les projets C/CLI utilisent le format de fichier vcxproj existant.
* Les projets C/CLI ne peuvent pas multitarget plusieurs plates-formes .NET. Si vous avez besoin de construire un projet CMD/CLI pour .NET Framework et .NET Core, utilisez des fichiers de projets distincts.
* .NET Core ne `-clr:pure` prend `-clr:safe` pas en `-clr:netcore` charge ou compilation, `-clr` seulement la nouvelle option (qui est équivalente à pour .NET Framework).

## <a name="port-a-ccli-project"></a>Projet de port a CMD/CLI

Pour effectuer un projet CMD/CLI à .NET Core, modifiez les modifications suivantes au fichier vcxproj. Ces étapes de migration diffèrent des étapes nécessaires pour d’autres types de projets, car les projets C/CLI n’utilisent pas de fichiers de projets de type SDK.

1. Remplacer `<CLRSupport>true</CLRSupport>` les `<CLRSupport>NetCore</CLRSupport>`propriétés par . Cette propriété est souvent dans les groupes de propriété spécifiques à la configuration, de sorte que vous devrez peut-être le remplacer à plusieurs endroits.
2. Remplacer `<TargetFrameworkVersion>` les `<TargetFramework>netcoreapp3.1</TargetFramework>`propriétés par .
3. Supprimer toutes les références `<Reference Include="System" />`cadre .NET (comme ). .NET Core SDK assemblages sont `<CLRSupport>NetCore</CLRSupport>`automatiquement référencés lors de l’utilisation .
4. Mettre à jour l’utilisation de l’API dans les fichiers cpp, au besoin, pour supprimer les API indisponibles pour .NET Core. Étant donné que les projets CMD/CLI ont tendance à être des couches interop assez minces, il n’y a souvent pas beaucoup de changements nécessaires. [L’analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) peut être utilisé pour identifier les API .NET non pris en charge utilisés par les binaires C/CLI tout comme avec les binaires purement gérés. Des lignes directrices pour déterminer la portabilité du code et la mise à jour des projets pour travailler avec les API de base .NET sont disponibles dans les directives de [portage de bibliothèque](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>Utilisation des formulaires WPF et Windows

Les projets .NET Core CMD/CLI peuvent utiliser les formulaires Windows et les API WPF. Pour utiliser ces API de bureau Windows, vous devez ajouter des références-cadres explicites aux bibliothèques d’interface utilisateur. Les projets de type SDK qui utilisent les API `Microsoft.NET.Sdk.WindowsDesktop` de bureau Windows font automatiquement référence aux bibliothèques-cadres nécessaires en utilisant le SDK. Étant donné que les projets CMD/CLI n’utilisent pas le format de projet de type SDK, ils doivent ajouter des références-cadres explicites lors du ciblage de .NET Core.

Pour utiliser les API Windows Forms, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Pour utiliser les API WPF, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Pour utiliser les formulaires Windows et les API WPF, ajoutez cette référence au fichier vcxproj :

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Actuellement, il n’est pas possible d’ajouter ces références à l’aide du gestionnaire de référence de Visual Studio. Au lieu de cela, mettre à jour le fichier du projet manuellement. Cette mise à jour peut être faite dans Visual Studio en déchargeant le projet, puis en éditant le fichier du projet. Vous pouvez également utiliser un autre éditeur comme VS Code.

## <a name="build-without-msbuild"></a>Construire sans MSBuild

Il est également possible de construire des projets CMD/CLI sans utiliser MSBuild. Suivez ces étapes pour construire un projet CMD/CLI pour .NET Core directement avec *cl.exe* et *link.exe*:

1. Lors de la compilation, passer `-clr:netcore` à *cl.exe*.
2. Référence nécessaire .NET Assemblages de référence de base.
3. Lors de la liaison, fournir le répertoire `LibPath` d’hôte de l’application .NET Core comme un (de sorte que *ijwhost.lib* peut être trouvé).
4. Copiez *ijwhost.dll* (de l’annuaire d’hôte de l’application .NET Core) à l’annuaire de sortie du projet.
5. Assurez-vous qu’un fichier [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) existe pour le premier composant de l’application qui exécutera le code géré. Si l’application dispose d’un point d’entrée géré, un `runtime.config` fichier sera créé et copié automatiquement. Si l’application a un point d’entrée `runtimeconfig.json` natif, cependant, vous devez créer un fichier pour la première bibliothèque C /CLI pour utiliser le temps d’exécution .NET Core.

## <a name="known-issues"></a>Problèmes connus

Il ya quelques problèmes connus à surveiller lors de la collaboration avec des projets C '/CLI ciblant .NET Core.

* Une référence-cadre WPF dans les projets .NET Core C/CLI provoque actuellement des avertissements supplémentaires sur l’impossibilité d’importer des symboles. Ces avertissements peuvent être ignorés en toute sécurité et doivent être corrigés bientôt.
* Si l’application a un point d’entrée natif, la bibliothèque CMD/CLI qui exécute d’abord le code géré a besoin d’un fichier [runtimeconfig.json.](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) Ce fichier config est utilisé lorsque le temps d’exécution .NET Core commence. Les projets C/CLI ne `runtimeconfig.json` créent pas encore de fichiers à l’heure de la construction, de sorte que le fichier doit être généré manuellement. Si une bibliothèque CMD/CLI est appelée à partir d’un point d’entrée géré, la bibliothèque CMD/CLI n’a pas besoin d’un `runtimeconfig.json` fichier (puisque l’assemblage du point d’entrée en aura un qui est utilisé lors du démarrage de l’exécution). Un fichier `runtimeconfig.json` d’échantillon simple est montré ci-dessous. Pour plus d’informations, voir les [spécifications sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

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
