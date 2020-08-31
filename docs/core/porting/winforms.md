---
title: Portage d’une application Windows Forms vers .NET Core
description: Explique comment porter un .NET Framework Windows Forms application vers .NET Core pour Windows.
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: 71bd5740e1ea380fdde86328a5aed71fded64765
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118544"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Comment porter une application de bureau Windows Forms sur .NET Core

Cet article explique comment déplacer votre application de bureau Windows Forms à partir de .NET Framework vers .NET Core 3,0 ou version ultérieure. Le kit de développement logiciel (SDK) .NET Core 3.0 prend en charge les applications Windows Forms. Windows Forms reste une infrastructure Windows qui s’exécute exclusivement sous Windows. Cet exemple utilise l’interface CLI du kit SDK .NET Core pour créer et gérer un projet.

Dans cet article, différents noms sont utilisés pour identifier les types de fichiers servant à la migration. Les fichiers de votre projet porteront d’autres noms ; faites-les correspondre mentalement à la liste ci-dessous :

| Fichier | Description |
| ---- | ----------- |
| **MyApps.sln** | Nom du fichier de solution. |
| **MyForms.csproj** | Nom du projet Windows Forms .NET Framework à porter. |
| **MyFormsCore.csproj** | Nom du nouveau projet .NET Core en création. |
| **MyAppCore.exe** | Exécutable de l’application Windows Forms .NET Core. |

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,5 ou ultérieure](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16) pour tout travail du concepteur que vous souhaitez effectuer. Nous vous recommandons d’effectuer la mise à jour vers la [dernière version de Visual Studio](https://visualstudio.microsoft.com/vs/).

  Installez les charges de travail Visual Studio suivantes :
  
  - Développement .NET Desktop
  - Développement multiplateforme .NET Core

- Un projet Windows Forms de travail dans une solution qui se génère et s’exécute sans problème.
- Projet codé en C#.

> [!NOTE]
> Les projets de Windows Forms .NET Core sont pris en charge dans Visual Studio 2019 et versions ultérieures. Le concepteur de Windows Forms .NET Core est pris en charge à partir de Visual Studio 2019 version 16,5.
>
> Pour activer le concepteur, accédez à **Outils**  >  **options**  >  **environnement**  >  **Aperçu fonctionnalités** , puis sélectionnez l’option **utiliser l’aperçu Windows Forms Designer pour les applications .net Core** .

### <a name="consider"></a>Consider

Voici les points à prendre en compte pour porter une application Windows Forms .NET Framework.

01. Vérifiez que votre application est une bonne candidate à la migration.

    Utilisez [l’Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour déterminer si votre projet sera migré vers .NET Core 3.0. S’il présente des problèmes avec .NET Core 3.0, l’analyseur permettra de les identifier.

01. Vous utilisez une autre version de Windows Forms.

    Lors de la sortie de .NET Core 3,0 Preview 1, Windows Forms a été ouvert Open source sur GitHub. Le code pour .NET Core Windows Forms est une fourche du code base Windows Forms .NET Framework. Il peut y avoir des différences qui empêchent le portage de l’application.

01. Le [Pack de compatibilité Windows][compat-pack] peut faciliter la migration.

    Certaines API disponibles dans .NET Framework ne le sont pas dans .NET Core 3.0. Le [Pack de compatibilité Windows][compat-pack] ajoute la plupart d’entre elles, ce qui peut faciliter la compatibilité de l’application Windows Forms avec .NET Core.

01. Mettez à jour les packages NuGet utilisés par votre projet.

    Il est toujours préférable d’utiliser les dernières versions des packages NuGet avant toute migration. Si votre application fait référence à des packages NuGet, passez à la dernière version. Vérifiez que votre application se génère correctement. En cas d’erreurs de package après la mise à niveau, passez à la dernière version du package qui ne casse pas votre code.

## <a name="create-a-new-sdk-project"></a>Créer un projet de kit SDK

Le nouveau projet .NET Core 3.0 doit se trouver dans un répertoire différent de celui du projet .NET Framework. S’ils sont dans le même répertoire, des conflits risquent de se produire avec les fichiers générés dans le répertoire **obj**. Dans cet exemple, créons un répertoire nommé **MyFormsAppCore** dans le répertoire **SolutionFolder** :

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Créons maintenant le projet **MyFormsCore.csproj** dans le répertoire **MyFormsAppCore**. Vous pouvez créer ce fichier manuellement avec l’éditeur de texte de votre choix. Collez-y le code XML suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Si vous ne souhaitez pas créer manuellement le fichier projet, vous pouvez utiliser Visual Studio ou le kit SDK .NET Core pour générer le projet. Il faut toutefois supprimer tous les fichiers générés par le modèle de projet à l’exception du fichier projet. Pour utiliser le kit SDK, exécutez la commande suivante à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Après la création de **MyFormsCore.csproj**, la structure de répertoires devrait se présenter ainsi :

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Ajoutez le projet **MyFormsCore. csproj** à **myapps. sln** avec Visual Studio ou le CLI .net core à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Corriger la génération d’informations sur l’assembly

Les projets Windows Forms créés avec .NET Framework comportent un fichier `AssemblyInfo.cs` qui contient des attributs d’assembly, comme la version de l’assembly à générer. Les projets de style kit SDK génèrent automatiquement ces informations selon le fichier projet du kit SDK. Ces deux types « d’informations sur l’assembly » entrent un conflit. Pour résoudre ce problème, désactivez la génération automatique, ce qui force le projet à utiliser votre fichier `AssemblyInfo.cs`.

Il y a trois paramètres à ajouter au nœud `<PropertyGroup>` principal.

- **GenerateAssemblyInfo**\
Si cette propriété est définie sur `false`, il ne génère pas les attributs d’assembly, ce qui permet d’éviter le conflit avec le fichier `AssemblyInfo.cs` du projet .NET Framework.

- **NomAssembly**\
La valeur de cette propriété est le binaire de sortie créé lors de la compilation. Il n’est pas nécessaire d’ajouter une extension au nom. Par exemple, `MyCoreApp` produit `MyCoreApp.exe`.

- **RootNamespace**\
Il s’agit de l’espace de noms utilisé par défaut par le projet, qui doit correspondre à celui du projet .NET Framework.

Ajoutez ces trois éléments au nœud `<PropertyGroup>` dans le fichier `MyFormsCore.csproj` :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Ajouter le code source

Actuellement, le projet **MyFormsCore.csproj** ne compile pas de code du tout. Par défaut, les projets .NET Core intègrent automatiquement tout le code source du répertoire actif et des répertoires enfants. Il faut configurer le projet pour inclure le code du projet du .NET Framework avec un chemin d’accès relatif. Si votre projet .NET Framework utilisait des fichiers **.resx** pour les icônes et les ressources des formulaires, ajoutez-les également.

Ajoutez le nœud `<ItemGroup>` suivant à votre projet. Chaque instruction inclut un modèle Glob de fichier qui comporte les répertoires enfants.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Vous pouvez également créer une entrée `<Compile>` ou `<EmbeddedResource>` pour chaque fichier de votre projet .NET Framework.

## <a name="add-nuget-packages"></a>Ajouter des packages NuGet

Ajoutez au projet .NET Core chacun des packages NuGet auxquels le projet .NET Framework fait référence.

Votre application Windows Forms .NET Framework comporte très probablement un fichier **packages.config** contenant la liste de tous les packages NuGet auxquels votre projet fait référence. Vous pouvez consulter cette liste pour déterminer quels packages NuGet ajouter au projet .NET Core. Par exemple, si le projet .NET Framework faisait référence aux packages NuGet `MetroFramework`, `MetroFramework.Design` et `MetroFramework.Fonts`, ajoutez-les au projet avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Les commandes précédentes ajoutent les références NuGet suivantes au projet **MyFormsCore.csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Porter des bibliothèques de contrôles

Les instructions à suivre pour porter un projet de bibliothèque de contrôles Windows Forms sont les mêmes que pour un projet d’application Windows Forms .NET Framework, à l’exception de quelques paramètres. Par ailleurs, la compilation s’effectue dans une bibliothèque plutôt qu’un exécutable. La différence entre le projet d’exécutable et le projet de bibliothèque, au-delà des chemins d’accès des modèles Glob de fichiers comportant le code source, est minime.

Reprenons l’exemple de l’étape précédente pour développer les projets et les fichiers de travail.

| Fichier | Description |
| ---- | ----------- |
| **MyApps.sln** | Nom du fichier de solution. |
| **MyControls.csproj** | Nom du projet de contrôles Windows Forms .NET Framework à porter. |
| **MyControlsCore.csproj** | Nom du nouveau projet de bibliothèque .NET Core en création. |
| **MyCoreControls.dll** | Bibliothèque de contrôles Windows Forms .NET Core. |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

Examinez les différences entre le projet `MyControlsCore.csproj` et le projet `MyFormsCore.csproj` créé précédemment.

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

Voici un exemple de fichier de projet de bibliothèque de contrôles Windows Forms .NET Core :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>

    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>

</Project>
```

Comme on peut le voir, le nœud `<OutputType>` a été supprimé, ce qui conduit le compilateur à générer par défaut une bibliothèque au lieu d’un exécutable. `<AssemblyName>` et `<RootNamespace>` ont été modifiés. En particulier, `<RootNamespace>` doit correspondre à l’espace de noms de la bibliothèque de contrôles Windows Forms portée. Enfin, les nœuds `<Compile>` et `<EmbeddedResource>` ont été ajustés pour pointer vers le dossier de la bibliothèque en question.

Ensuite, dans le projet .NET Core **MyFormsCore. csproj** principal, ajoutez une référence à la nouvelle bibliothèque de contrôles de Windows Forms .net core. avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>Problèmes de compilation

Si avez des difficultés à compiler vos projets, c’est peut-être le signe que vous utilisez des API Windows disponibles dans .NET Framework et non dans .NET Core. Vous pouvez essayer d’ajouter le package NuGet [Pack de compatibilité Windows][compat-pack] à votre projet. Ce package, qui s’exécute seulement sur Windows, ajoute environ 20 000 API Windows aux projets .NET Core et .NET Standard.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Concepteur Windows Forms

Comme nous l’avons indiqué dans cet article, Visual Studio 2019 ne prend en charge le Concepteur Windows Forms que dans les projets .NET Framework. En créant un projet .NET Core côte à côte, vous pouvez tester votre projet avec .NET Core tout en utilisant le projet .NET Framework pour concevoir des formulaires. Le fichier de solution comporte à la fois les projets .NET Framework et .NET Core. Ajoutez et concevez vos formulaires et vos contrôles dans le projet .NET Framework ; à partir des modèles Glob de fichier que nous avons ajoutés aux projets .NET Core, les nouveaux fichiers et les fichiers modifiés sont automatiquement intégrés au projet .NET Core.

Dès que Visual Studio 2019 prendra en charge le Concepteur Windows Forms, vous pourrez copier/coller le contenu de votre fichier projet .NET Core dans le fichier projet .NET Framework, puis supprimer les modèles Glob de fichier ajoutés avec les éléments `<Source>` et `<EmbeddedResource>`. Résolvez le chemin d’accès des références de projet utilisées par votre application. Le projet .NET Framework est ainsi mis à niveau en un projet .NET Core.

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur [les modifications avec rupture d' .NET Framework à .net Core](../compatibility/fx-core.md).
- En savoir plus sur le [Pack de compatibilité Windows][compat-pack].
- Regardez une [vidéo sur le portage](https://www.youtube.com/watch?v=upVQEUc_KwU) de projets Windows Forms .NET Framework vers .NET Core.

[compat-pack]: windows-compat-pack.md
