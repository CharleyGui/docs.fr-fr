---
title: Porter une application WPF sur .NET Core 3.0
description: Explique comment porter une application .NET Framework Windows Presentation Foundation sur .NET Core 3.0 pour Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 1528e578a978de38998b3f3f4b7beb72ff7422d4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117063"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Procédure : Porter une application de bureau WPF sur .NET Core

Cet article explique comment porter votre application de bureau Windows Presentation Foundation (WPF) du .NET Framework vers .NET Core 3.0. Le SDK .NET Core 3.0 prend en charge les applications WPF. WPF reste un framework Windows qui s’exécute exclusivement sur Windows. Cet exemple utilise l’interface CLI du kit SDK .NET Core pour créer et gérer un projet.

Dans cet article, différents noms sont utilisés pour identifier les types de fichiers servant à la migration. Les fichiers de votre projet porteront d’autres noms ; faites-les correspondre mentalement à la liste ci-dessous :

| Fichier | Description |
| ---- | ----------- |
| **MyApps.sln** | Nom du fichier de solution. |
| **MyWPF.csproj** | Nom du projet WPF .NET Framework à porter. |
| **MyWPFCore.csproj** | Nom du nouveau projet .NET Core en création. |
| **MyAppCore.exe** | Exécutable de l’application WPF .NET Core. |

>[!IMPORTANT]
>Bien que cet article utilise C# comme langage cible, les étapes sont les mêmes pour VB.NET, à ceci près que VB.NET utilise des fichiers *.vbproj* et *.vb* au lieu de fichiers *.csproj* et *.cs*, respectivement.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour tout le travail de conception.

  Installez les charges de travail Visual Studio suivantes :
  - Développement .NET Desktop
  - Développement multiplateforme .NET

- Un projet WPF de travail dans une solution qui se génère et s’exécute sans problème.
- Installez la dernière préversion de [.NET Core 3.0](https://aka.ms/netcore3download).

>[!NOTE]
>**Visual Studio 2017** ne prend pas en charge les projets .NET Core 3.0. **Visual Studio 2019** prend en charge les projet .NET Core 3.0, mais offre une prise en charge limitée du concepteur visuel WPF .NET Core. Pour utiliser un concepteur visuel entièrement pris en charge, votre solution doit comporter un projet WPF .NET Framework qui partage ses fichiers avec le projet .NET Core.

### <a name="consider"></a>Consider

Voici les points à prendre en compte pour porter une application WPF .NET Framework.

01. Vérifiez que votre application est une bonne candidate à la migration.

    Utilisez [l’Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour déterminer si votre projet sera migré vers .NET Core 3.0. S’il présente des problèmes avec .NET Core 3.0, l’analyseur permettra de les identifier.

01. Vous utilisez une autre version de WPF.

    Lors de la sortie de .NET Core 3.0 Preview 1, WPF est devenu open source sur GitHub. Le code de WPF .NET Core est une duplication du codebase WPF .NET Framework. Il peut y avoir des différences qui empêchent le portage de l’application.

01. Le [Pack de compatibilité Windows][compat-pack] peut faciliter la migration.

    Certaines API disponibles dans .NET Framework ne le sont pas dans .NET Core 3.0. Le [Pack de compatibilité Windows][compat-pack] ajoute la plupart d’entre elles, ce qui peut faciliter la compatibilité de l’application WPF avec .NET Core.

01. Mettez à jour les packages NuGet utilisés par votre projet.

    Il est toujours préférable d’utiliser les dernières versions des packages NuGet avant toute migration. Si votre application fait référence à des packages NuGet, passez à la dernière version. Vérifiez que votre application se génère correctement. En cas d’erreurs de package après la mise à niveau, passez à la dernière version du package qui ne casse pas votre code.

01. Visual Studio 2019 ne gère pas encore le Concepteur WPF pour .NET Core 3.0.

    Pour le moment, vous devez conserver le fichier projet WPF actuel du .NET Framework pour pouvoir utiliser le Concepteur WPF dans Visual Studio.

## <a name="create-a-new-sdk-project"></a>Créer un projet de kit SDK

Le nouveau projet .NET Core 3.0 doit se trouver dans un répertoire différent de celui du projet .NET Framework. S’ils sont dans le même répertoire, des conflits risquent de se produire avec les fichiers générés dans le répertoire **obj**. Dans cet exemple, vous allez créer un répertoire nommé **MyWPFAppCore** dans le répertoire **SolutionFolder** :

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Ensuite, vous avez besoin de créer le projet **MyWPFCore.csproj** dans le répertoire **MyWPFAppCore**. Vous pouvez créer ce fichier manuellement avec l’éditeur de texte de votre choix. Collez-y le code XML suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Si vous ne souhaitez pas créer manuellement le fichier projet, vous pouvez utiliser Visual Studio ou le kit SDK .NET Core pour générer le projet. Il faut toutefois supprimer tous les fichiers générés par le modèle de projet à l’exception du fichier projet. Pour utiliser le kit SDK, exécutez la commande suivante à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Une fois **MyWPFCore.csproj** créé, la structure de répertoires doit se présenter ainsi :

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Ajoutez le projet **MyWPFCore.csproj** à **MyApps.sln** avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Corriger la génération d’informations sur l’assembly

Les projets Windows Presentation Foundation créés avec le .NET Framework comportent un fichier `AssemblyInfo.cs` qui contient des attributs d’assembly, comme la version de l’assembly à générer. Les projets de style kit SDK génèrent automatiquement ces informations selon le fichier projet du kit SDK. Ces deux types « d’informations sur l’assembly » entrent un conflit. Pour résoudre ce problème, désactivez la génération automatique, ce qui force le projet à utiliser votre fichier `AssemblyInfo.cs`.

Il y a trois paramètres à ajouter au nœud `<PropertyGroup>` principal. 

- **GenerateAssemblyInfo**\
Si cette propriété est définie sur `false`, il ne génère pas les attributs d’assembly, ce qui permet d’éviter le conflit avec le fichier `AssemblyInfo.cs` du projet .NET Framework.

- **AssemblyName**\
La valeur de cette propriété est le binaire de sortie créé lors de la compilation. Il n’est pas nécessaire d’ajouter une extension au nom. Par exemple, `MyCoreApp` produit `MyCoreApp.exe`.

- **RootNamespace**\
Il s’agit de l’espace de noms utilisé par défaut par le projet, qui doit correspondre à celui du projet .NET Framework.

Ajoutez ces trois éléments au nœud `<PropertyGroup>` dans le fichier `MyWPFCore.csproj` :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Ajouter le code source
Actuellement, le projet **MyWPFCore.csproj** ne compile pas de code du tout. Par défaut, les projets .NET Core intègrent automatiquement tout le code source du répertoire actif et des répertoires enfants. Il faut configurer le projet pour inclure le code du projet du .NET Framework avec un chemin d’accès relatif. Si votre projet .NET Framework utilisait des fichiers **.resx** pour les icônes et les ressources des fenêtres et contrôles, ajoutez-les également. 

Le premier nœud `<ItemGroup>` que vous devez ajouter à votre projet contient le fichier **App.xaml** qui représente la configuration de démarrage et les ressources que votre application utilise. Le fichier **App.xaml** est également assorti d’un fichier **App.xaml.cs**, mais il sera automatiquement inclus dans un autre `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Ajoutez ensuite le nœud `<ItemGroup>` suivant à votre projet. Chaque instruction inclut un modèle Glob de fichier qui comporte les répertoires enfants. Ce modèle inclut le code source de votre projet, tous les fichiers de paramètres et toutes les ressources. Le répertoire **obj** est explicitement exclu.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Ensuite, incluez un autre nœud `<ItemGroup>` qui contient une entrée `<Page>` pour chaque fichier **xaml** contenu dans votre projet, mis à part le fichier **App.xaml**. Ces fichiers contiennent toutes les fenêtres, pages et ressources qui sont au format **xaml**. Vous ne pouvez pas utiliser un modèle Glob ici et vous devez ajouter une entrée pour chaque fichier et indiquer le `<Generator>` utilisé.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Ajouter des packages NuGet

Ajoutez au projet .NET Core chacun des packages NuGet auxquels le projet .NET Framework fait référence. 

Votre application WPF .NET Framework comporte très probablement un fichier **packages.config** contenant la liste de tous les packages NuGet auxquels votre projet fait référence. Vous pouvez consulter cette liste pour déterminer quels packages NuGet ajouter au projet .NET Core. Par exemple, si le projet .NET Framework fait référence au package NuGet `MahApps.Metro`, ajoutez-le au projet avec Visual Studio. Vous pouvez aussi ajouter la référence au package avec l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

La commande précédente ajoute la référence NuGet suivante au projet **MyWPFCore.csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problèmes de compilation

Si avez des difficultés à compiler vos projets, c’est peut-être le signe que vous utilisez des API Windows disponibles dans .NET Framework et non dans .NET Core. Vous pouvez essayer d’ajouter le package NuGet [Pack de compatibilité Windows][compat-pack] à votre projet. Ce package, qui s’exécute seulement sur Windows, ajoute environ 20 000 API Windows aux projets .NET Core et .NET Standard.

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

La commande précédente ajoute le code suivant au projet **MyWPFCore.csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>Concepteur WPF

Comme nous l’avons indiqué dans cet article, Visual Studio 2019 ne prend en charge le Concepteur WPF que dans les projets .NET Framework. En créant un projet .NET Core côte à côte, vous pouvez tester votre projet avec .NET Core tout en utilisant le projet .NET Framework pour concevoir des formulaires. Le fichier de solution comporte à la fois les projets .NET Framework et .NET Core. Ajoutez et concevez vos formulaires et vos contrôles dans le projet .NET Framework ; à partir des modèles Glob de fichier que nous avons ajoutés aux projets .NET Core, les nouveaux fichiers et les fichiers modifiés sont automatiquement intégrés au projet .NET Core.

Dès que Visual Studio 2019 prendra en charge le Concepteur WPF, vous pourrez copier/coller le contenu de votre fichier projet .NET Core dans le fichier projet .NET Framework, puis supprimer les modèles Glob de fichier ajoutés avec les éléments `<Source>` et `<EmbeddedResource>`. Résolvez le chemin d’accès des références de projet utilisées par votre application. Le projet .NET Framework est ainsi mis à niveau en un projet .NET Core.

## <a name="next-steps"></a>Étapes suivantes

- Découvrez-en plus sur le [Pack de compatibilité Windows][compat-pack].
- Regardez une [vidéo sur le portage](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) de projets WPF .NET Framework vers .NET Core.

[compat-pack]: windows-compat-pack.md
