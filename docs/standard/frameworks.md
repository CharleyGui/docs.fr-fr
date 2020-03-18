---
title: Cadres cibles dans les projets de style SDK - .NET
description: Découvrez les frameworks cibles pour les applications et bibliothèques .NET Core.
ms.date: 12/03/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 33beb5606cbf857cc41b739f256482b0298f1fb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400553"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>Cadres cibles dans les projets de type SDK

Quand vous ciblez un framework dans une application ou une bibliothèque, vous spécifiez l’ensemble d’API que vous souhaitez rendre accessibles à l’application ou à la bibliothèque. Vous spécifiez le framework cible dans votre fichier projet à l’aide des monikers du framework cible (TFM).

Une application ou une bibliothèque peut cibler une version de [.NET Standard](net-standard.md). Les versions .NET Standard représentent des ensembles d’API standard sur toutes les implémentations de .NET. Par exemple, une bibliothèque peut cibler .NET Standard 1.6 et accéder aux API qui fonctionnent sur .NET Core et .NET Framework en utilisant la même base de code.

Une application ou une bibliothèque peut également cibler une implémentation spécifique de .NET pour accéder aux API spécifiques à l’implémentation. Ainsi, une application qui cible Xamarin.iOS (par exemple, `Xamarin.iOS10`) accède à des wrappers d’API iOS fournis par Xamarin pour iOS 10, ou une application qui cible la plateforme Windows universelle (UWP, `uap10.0`) a accès aux API de compilation pour les appareils qui exécutent Windows 10.

Pour certains frameworks cibles (par exemple, .NET Framework), les API sont définies par les assemblys que le framework installe sur un système et peuvent inclure des API de framework d’application (par exemple, ASP.NET).

Pour les frameworks cibles basés sur le package (par exemple, .NET Standard et .NET Core), les API sont définies par les packages inclus dans l’application ou la bibliothèque. Un *métapackage* est un package NuGet qui n’a aucun contenu propre, mais qui est une liste de dépendances (autres packages). Un framework cible basé sur un package NuGet spécifie implicitement un métapackage qui référence tous les packages constituant le framework.

## <a name="latest-target-framework-versions"></a>Versions les plus récentes des frameworks cibles

Le tableau ci-dessous définit les frameworks cibles les plus courants, la façon dont ils sont référencés et la version de [.NET Standard](net-standard.md) qu’ils implémentent. Ces versions de framework cible sont les dernières versions stables. Les préversions ne sont pas mentionnées. Un moniker du framework cible est un format de jeton standardisé pour la spécification du framework cible d’une bibliothèque ou d’une application .NET.

| Framework cible      | Latest <br/> Version stable | Moniker du Framework cible | Implémenté <br/> Version .NET Standard |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.1                         | netstandard2.1                 | N/A                                     |
| .NET Core             | 3.1                         | netcoreapp3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2                                     |

## <a name="supported-target-framework-versions"></a>Versions de framework cible prises en charge

Un framework cible est généralement référencé par un TFM. Le tableau suivant présente les frameworks cibles pris en charge par le SDK .NET Core et le client NuGet. Les équivalents sont indiqués entre crochets. Par exemple, `win81` est un TFM équivalent de `netcore451`.

| Framework cible           | TFM |
| -------------------------- | --- |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0<br>netstandard2.1 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2<br>netcoreapp3.0<br>netcoreapp3.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Store              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Plateforme Windows universelle | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Comment spécifier des frameworks cibles

Les frameworks cibles sont spécifiés dans votre fichier projet. Quand vous spécifiez un framework cible unique, utilisez l’élément **TargetFramework**. Le fichier de projet d’application de console suivant montre comment cibler .NET Core 3.0 :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Quand vous spécifiez plusieurs frameworks cibles, vous pouvez référencer conditionnellement des assemblys pour chaque framework cible. Dans votre code, vous pouvez effectuer une compilation conditionnelle par rapport à ces assemblys en utilisant des symboles de préprocesseur avec la structure logique *if-then-else*.

Le fichier projet de bibliothèque suivant cible des API de .NET Standard (`netstandard1.4`) et des API de .NET Framework (`net40` et `net45`). Utilisez l’élément pluriel **TargetFrameworks** avec plusieurs frameworks cibles. Notez la façon dont les attributs `Condition` incluent les packages spécifiques à l’implémentation quand la bibliothèque est compilée pour les deux TFM .NET Framework :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

Au sein de votre application ou bibliothèque, vous écrivez du code conditionnel à compiler pour chaque framework cible :

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Le système de construction est au courant des symboles de préprocesseur représentant les cadres cibles indiqués dans le tableau [des versions-cadres cibles pris](#supported-target-framework-versions) en charge lorsque vous utilisez des projets de type SDK. Quand vous utilisez un symbole représentant un TFM .NET Standard ou .NET Core, remplacez le point par un trait de soulignement et remplacez les lettres minuscules par des lettres majuscules (par exemple, le symbole pour `netstandard1.4` est `NETSTANDARD1_4`).

La liste complète des symboles de préprocesseur pour les frameworks cibles de .NET Core est la suivante :

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Frameworks cibles dépréciés

Les frameworks cibles suivants sont dépréciés. Les packages ciblant ces frameworks cibles doivent migrer vers les versions de remplacement indiquées.

| TFM déprécié                                                                             | Remplacement |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| win                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Voir aussi

- [Packages, métapackages et frameworks](../core/packages.md)
- [Développer des bibliothèques avec des outils multiplateformes](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Gestion des versions de .NET Core](../core/versions/index.md)
- [dotnet/standard GitHub repository](https://github.com/dotnet/standard) (Dépôt GitHub dotnet/standard)
- [NuGet Tools GitHub Repository](https://github.com/joelverhagen/NuGetTools) (Dépôt GitHub des outils NuGet)
- [Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (Profils de framework dans .NET)
