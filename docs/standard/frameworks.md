---
title: Frameworks cibles dans des projets de type SDK-.NET
description: En savoir plus sur les frameworks cibles pour les applications et les bibliothèques .NET.
ms.date: 09/08/2020
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 85bc05f07cfcc5f59a8a27790ee3d78a497cecdc
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223466"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>Frameworks cibles dans les projets de style SDK

Quand vous ciblez un framework dans une application ou une bibliothèque, vous spécifiez l’ensemble d’API que vous souhaitez rendre accessibles à l’application ou à la bibliothèque. Vous spécifiez la version cible de .NET Framework dans votre fichier projet à l’aide des monikers du Framework cible (TFM).

Une application ou une bibliothèque peut cibler une version de [.NET Standard](net-standard.md). Les versions .NET Standard représentent des ensembles d’API standard sur toutes les implémentations de .NET. Par exemple, une bibliothèque peut cibler .NET Standard 1.6 et accéder aux API qui fonctionnent sur .NET Core et .NET Framework en utilisant la même base de code.

Une application ou une bibliothèque peut également cibler une implémentation spécifique de .NET pour accéder aux API spécifiques à l’implémentation. Par exemple, une application qui cible Xamarin. iOS (par exemple, `Xamarin.iOS10` ) a accès aux wrappers d’API iOS fournis par Xamarin pour iOS 10, ou une application qui cible plateforme Windows universelle (UWP `uap10.0` ) a accès aux API qui se compilent pour les appareils qui exécutent Windows 10.

Pour certains frameworks cibles (par exemple, .NET Framework), les API sont définies par les assemblys que le Framework installe sur un système et peuvent inclure des API de Framework d’application (par exemple, ASP.NET).

Pour les frameworks cibles basés sur le package (par exemple, .NET Standard et .NET Core), les API sont définies par les packages inclus dans l’application ou la bibliothèque. Un *métapackage* est un package NuGet qui n’a aucun contenu propre, mais qui est une liste de dépendances (autres packages). Un framework cible basé sur un package NuGet spécifie implicitement un métapackage qui référence tous les packages constituant le framework.

## <a name="latest-versions"></a>Dernières versions

Le tableau suivant définit les frameworks cibles les plus courants, la façon dont ils sont référencés et la version de [.NET standard](net-standard.md) qu’ils implémentent. Ces versions de framework cible sont les dernières versions stables. Les préversions ne sont pas mentionnées. Un moniker de Framework cible (TFM) est un format de jeton standardisé pour la spécification de la version cible de .NET Framework d’une application ou d’une bibliothèque .NET.

| Version cible de .NET Framework      | Latest <br/> version stable | Moniker du Framework cible (TFM) | Implémenté <br/> Version de .NET Standard |
| :-: | :-: | :-: | :-: |
| .NET Standard         | 2.1                         | netstandard 2.1                 | N/A                                     |
| .NET Core             | 3.1                         | netcoreapp 3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-frameworks"></a>Frameworks cibles pris en charge

Un framework cible est généralement référencé par un TFM. Le tableau suivant présente les frameworks cibles pris en charge par le kit de développement logiciel (SDK) .NET et le client NuGet. Les équivalents sont indiqués entre crochets. Par exemple, `win81` est un TFM équivalent de `netcore451`.

| Framework cible           | TFM |
| -------------------------- | --- |
| .NET 5 (et .NET Core)     | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2<br>netcoreapp 3.0<br>netcoreapp 3.1<br>.net 5.0 * |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0<br>netstandard 2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Store              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Plateforme Windows universelle | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

\* .NET 5,0 et versions ultérieures TFM incluent des variantes spécifiques au système d’exploitation. Pour plus d’informations, consultez la section suivante, [TFM propre au système d’exploitation .net 5](#net-5-os-specific-tfms).

### <a name="net-5-os-specific-tfms"></a>TFM spécifique à .NET 5

Pour chaque TFM .NET 5,0 et versions ultérieures, par exemple, `net5.0` il existe des variantes TFM qui incluent des liaisons spécifiques au système d’exploitation. Ces variations sont indiquées dans le tableau suivant.

| Format propre au système d’exploitation | Exemple        |
|--------------------|----------------|
| \<base-tfm>-Android | .net 5.0-Android |
| \<base-tfm>-iOS     | net 5.0-iOS     |
| \<base-tfm>-MacOS   | .net 5.0-MacOS   |
| \<base-tfm>-TVos    | .net 5.0-TVos    |
| \<base-tfm>-Watchos | net 5.0-Watchos |
| \<base-tfm>7.5.0 | .net 5.0-Windows |

Vous pouvez également spécifier une version de système d’exploitation facultative, par exemple `net5.0-ios12.0` .

Pour plus d’informations sur les TFM de .NET 5, consultez [Target Framework Names in .net 5](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md).

## <a name="how-to-specify-a-target-framework"></a>Comment spécifier une version cible de .NET Framework

Les frameworks cibles sont spécifiés dans un fichier projet. Quand vous spécifiez un framework cible unique, utilisez l’élément **TargetFramework**. Le fichier de projet d’application console suivant montre comment cibler .NET 5,0 :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Quand vous spécifiez plusieurs frameworks cibles, vous pouvez référencer conditionnellement des assemblys pour chaque framework cible. Dans votre code, vous pouvez effectuer une compilation conditionnelle par rapport à ces assemblys en utilisant des symboles de préprocesseur avec la structure logique *if-then-else*.

Le projet de bibliothèque suivant cible les API de .NET Standard ( `netstandard1.4` ) et .NET Framework ( `net40` et `net45` ). Utilisez l’élément pluriel **TargetFrameworks** avec plusieurs frameworks cibles. Les `Condition` attributs incluent des packages spécifiques à l’implémentation lorsque la bibliothèque est compilée pour les deux .NET Framework TFM :

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

Dans votre bibliothèque ou votre application, vous écrivez du code conditionnel à l’aide de [directives de préprocesseur](../csharp/language-reference/preprocessor-directives/preprocessor-if.md) à compiler pour chaque Framework cible :

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

Le système de génération tient compte des symboles de préprocesseur représentant les frameworks cibles affichés dans le tableau [versions de Framework cible prises en charge](#supported-target-frameworks) lorsque vous utilisez des projets de type SDK. Quand vous utilisez un symbole qui représente une .NET Standard, .NET Core ou .NET 5 TFM, remplacez les points et les traits d’Union par un trait de soulignement et remplacez les lettres minuscules par des majuscules (par exemple, le symbole de `netstandard1.4` est `NETSTANDARD1_4` ).

La liste complète des symboles de préprocesseur pour les frameworks cibles .NET est la suivante :

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Frameworks cibles dépréciés

Les frameworks cibles suivants sont dépréciés. Les packages qui ciblent ces frameworks cibles doivent migrer vers les remplacements indiqués.

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

- [Développer des bibliothèques avec des outils multiplateformes](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Gestion des versions de .NET Core](../core/versions/index.md)
- [dotnet/standard GitHub repository](https://github.com/dotnet/standard) (Dépôt GitHub dotnet/standard)
- [NuGet Tools GitHub Repository](https://github.com/joelverhagen/NuGetTools) (Dépôt GitHub des outils NuGet)
- [Framework Profiles in .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html) (Profils de framework dans .NET)
