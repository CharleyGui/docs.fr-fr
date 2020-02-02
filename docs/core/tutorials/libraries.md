---
title: Développer des bibliothèques avec le CLI .NET Core
description: Découvrez comment créer des bibliothèques .NET Core à l’aide de l’CLI .NET Core. Vous allez créer une bibliothèque prenant en charge plusieurs frameworks.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: a7c0175d29f483571578b58d698dd790cf66f7f4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920443"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>Développer des bibliothèques avec le CLI .NET Core

Cet article explique comment écrire des bibliothèques pour .NET à l’aide de l’CLI .NET Core. L’interface CLI fournit une expérience efficace et de bas niveau qui fonctionne sur tous les systèmes d’exploitation pris en charge. Vous pouvez toujours créer des bibliothèques avec Visual Studio, et si c’est ce que vous préférez, [consultez le guide Visual Studio](library-with-visual-studio.md).

## <a name="prerequisites"></a>Prerequisites

[Le SDK .NET Core et l’interface CLI](https://dotnet.microsoft.com/download) doivent être installés sur votre ordinateur.

Pour accéder aux sections de ce document concernant les versions du .NET Framework, vous devez installer le [.NET Framework](https://dotnet.microsoft.com) sur un ordinateur Windows.

En outre, si vous souhaitez prendre en charge des cibles de .NET Framework plus anciennes, vous devez installer des packs de ciblage ou des packs de développement à partir de la [page des Archives de téléchargement .net](https://dotnet.microsoft.com/download/archives). Reportez-vous au tableau suivant :

| Version du .NET Framework | À télécharger                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Pack de ciblage .NET Framework 4.6.1                    |
| 4.6                    | Pack de ciblage .NET Framework 4.6                      |
| 4.5.2                  | Pack du développeur .NET Framework 4.5.2                    |
| 4.5.1                  | Pack du développeur .NET Framework 4.5.1                    |
| 4,5                    | SDK Windows pour Windows 8         |
| 4.0                    | SDK pour Windows 7 et .NET Framework 4         |
| 2.0, 3.0 et 3.5      | Runtime .NET Framework 3.5 SP1 (ou version Windows 8+) |

## <a name="how-to-target-the-net-standard"></a>Comment cibler .NET Standard

Si vous n’êtes pas familiarisé avec .NET Standard, reportez-vous à [.NET standard](../../standard/net-standard.md) pour en savoir plus.

Dans cet article, il existe un tableau qui mappe .NET Standard versions à différentes implémentations :

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Voici ce que signifie ce tableau dans le processus de création d’une bibliothèque :

La version de .NET Standard que vous choisissez est un compromis entre l’accès aux API les plus récentes et la possibilité de cibler davantage d’implémentations .NET et de versions de .NET Standard. Vous contrôlez la plage de versions et de plateformes ciblables en choisissant une version de `netstandardX.X` (où `X.X` est un numéro de version) et en l’ajoutant à votre fichier projet (`.csproj` ou `.fsproj`).

Vous avez trois options principales pour cibler .NET Standard, en fonction de vos besoins.

1. Vous pouvez utiliser la version par défaut de .NET Standard fournie par les modèles, `netstandard1.4`, qui vous donne accès à la plupart des API sur .NET Standard tout en étant toujours compatibles avec UWP, .NET Framework 4.6.1 et .NET Standard 2,0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Vous pouvez utiliser une version inférieure ou supérieure de .NET Standard en modifiant la valeur dans le nœud `TargetFramework` de votre fichier projet.

    Les versions .NET standard sont à compatibilité descendante. Cela signifie que les bibliothèques `netstandard1.0` s’exécutent sur les plateformes `netstandard1.1` et versions ultérieures. Toutefois, il n’existe pas de compatibilité ascendante. Les plateformes de .NET Standard inférieures ne peuvent pas faire référence à des plateformes supérieures. Cela signifie que les bibliothèques `netstandard1.0` ne peuvent pas cibler des bibliothèques de référence ciblant `netstandard1.1` ou une version ultérieure. Sélectionnez la version Standard qui offre une bonne combinaison entre les API et la prise en charge de plateformes pour vos besoins. Nous vous recommandons d’utiliser `netstandard1.4` pour l’instant.

3. Si vous souhaitez cibler .NET Framework versions 4,0 ou antérieures, ou si vous souhaitez utiliser une API disponible dans .NET Framework mais pas dans .NET Standard (par exemple, `System.Drawing`), lisez les sections suivantes et découvrez comment effectuer une MULTICIBLAGE.

## <a name="how-to-target-net-framework"></a>Comment cibler .NET Framework

> [!NOTE]
> Ces instructions supposent que vous avez .NET Framework installé sur votre ordinateur. Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.

N’oubliez pas que certaines des versions de .NET Framework utilisées ici ne sont plus prises en charge. Reportez-vous au [Forum aux questions sur la politique de support de Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) concernant les versions non prises en charge.

Si vous voulez atteindre le nombre maximal de développeurs et de projets, utilisez .NET Framework 4,0 comme cible de référence. Pour cibler .NET Framework, commencez par utiliser le moniker du Framework cible (TFM) approprié qui correspond à la version .NET Framework que vous souhaitez prendre en charge.

| Version du .NET Framework | TFM      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| .NET Framework 4.7     | `net47`  |
| .NET Framework 4.8     | `net48`  |

Insérez ensuite ce Moniker du Framework cible dans la section `TargetFramework` de votre fichier projet. Par exemple, voici comment écrire une bibliothèque qui cible .NET Framework 4,0 :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

Et voilà ! Bien que cela soit compilé uniquement pour .NET Framework 4, vous pouvez utiliser la bibliothèque sur des versions plus récentes de .NET Framework.

## <a name="how-to-multitarget"></a>Comment multicibler

> [!NOTE]
> Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur. Reportez-vous à la section [Prérequis](#prerequisites) pour savoir quelles dépendances doivent être installées et à partir d’où les télécharger.

Vous devrez peut-être cibler des versions antérieures du .NET Framework si votre projet prend en charge à la fois .NET Framework et .NET Core. Dans ce scénario, si vous voulez utiliser des API et des constructions de langage plus récentes pour des cibles plus récentes, utilisez des directives `#if` dans votre code. Vous pouvez aussi avoir besoin d’ajouter différents packages et différentes dépendances pour chaque plateforme que vous ciblez pour inclure les différentes API nécessaires à chaque cas.

Supposons, par exemple, que vous avez une bibliothèque qui effectue des opérations réseau sur HTTP. Pour .NET Standard et les versions .NET Framework 4.5 ou ultérieures, vous pouvez utiliser la classe `HttpClient` à partir de l’espace de noms `System.Net.Http`. Toutefois, les versions antérieures du .NET Framework ne disposent pas de la classe `HttpClient`. Vous pourriez donc utiliser la classe `WebClient` à partir de l’espace de noms `System.Net` à la place.

Voici à quoi peut ressembler votre fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

Notez trois changements majeurs ici :

1. Le nœud `TargetFramework` a été remplacé par `TargetFrameworks`, et trois Monikers du Framework cible sont exprimés à l’intérieur.
1. Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net40` dans une référence .NET Framework.
1. Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net45` dans deux références .NET Framework.

Le système de build est informé des symboles de préprocesseur suivants utilisés dans les directives `#if`:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Voici un exemple d’utilisation de la compilation conditionnelle par cible :

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Si vous générez ce projet avec `dotnet build`, notez la présence de trois répertoires sous le dossier `bin/` :

```
net40/
net45/
netstandard1.4/
```

Chacun d’entre eux contient les fichiers `.dll` pour chaque cible.

## <a name="how-to-test-libraries-on-net-core"></a>Comment tester les bibliothèques sur .NET Core

Il est important de pouvoir effectuer des tests sur plusieurs plateformes. Vous pouvez utiliser [xUnit](https://xunit.github.io/) ou MSTest dans leur version d’origine. Les deux conviennent parfaitement à la réalisation de tests unitaires sur votre bibliothèque sur .NET Core. La façon dont vous configurez votre solution avec des projets de test dépend de la [structure de votre solution](#structuring-a-solution). L’exemple suivant part du principe que les répertoires de test et source résident dans le même répertoire de premier niveau.

> [!NOTE]
> Cela utilise certaines commandes [CLI .net Core](../tools/index.md) . Pour plus d’informations, consultez [dotnet new](../tools/dotnet-new.md) et [dotnet sln](../tools/dotnet-sln.md).

1. Configurez votre solution. Pour cela, utilisez la commande suivante :

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Cette commande crée des projets et les relie dans une solution. Votre répertoire pour `SolutionWithSrcAndTest` doit ressembler à ceci :

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Accédez au répertoire du projet de test et ajoutez une référence à `MyProject.Test` à partir de `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Restaurez les packages et générez les projets :

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Exécutez la commande `dotnet test` pour vérifier que xUnit s’exécute. Si vous avez choisi d’utiliser MSTest, le Test Runner de console MSTest doit s’exécuter à la place.

Et voilà ! Vous pouvez maintenant tester votre bibliothèque sur toutes les plateformes à l’aide d’outils en ligne de commande. Maintenant que vous avez tout configuré, le test de votre bibliothèque est très simple :

1. Apportez des modifications à votre bibliothèque.
1. Exécutez les tests à partir de la ligne de commande, dans votre répertoire de test, avec la commande `dotnet test`.

Votre code est automatiquement régénéré quand vous appelez la commande `dotnet test`.

## <a name="how-to-use-multiple-projects"></a>Comment utiliser plusieurs projets

Les bibliothèques plus volumineuses ont souvent besoin de placer des fonctionnalités dans différents projets.

Imaginez que vous vouliez créer une bibliothèque pouvant être utilisée dans idiomatique C# et F#. Cela signifierait que les consommateurs de votre bibliothèque le consomment de manière naturelle C# à F#ou. Par exemple, en C#, vous pouvez utiliser la bibliothèque de la façon suivante :

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

En F#, le code peut se présenter comme suit :

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Les scénarios de consommation tels que celui-ci signifient que les API auxquelles vous accédez ont une structure différente en C# et F#.  Pour réaliser ceci, il est courant de factoriser toute la logique d’une bibliothèque dans un projet principal et d’avoir des projets C# et F# définissant les couches API qui effectuent des appels à ce projet principal.  Le reste de la section utilise les noms suivants :

* **AwesomeLibrary. Core** : projet principal qui contient toute la logique de la bibliothèque
* **AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#
* **AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en F#

Vous pouvez exécuter les commandes suivantes dans votre terminal pour produire la même structure que ce guide :

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Cela permet d’ajouter les trois projets ci-dessus et un fichier solution qui les lie. La création du fichier solution et la liaison de projets vous permettent de restaurer et de générer des projets à partir d’un niveau supérieur.

### <a name="project-to-project-referencing"></a>Références entre projets

La meilleure façon de référencer un projet consiste à utiliser l’interface CLI .NET Core pour ajouter une référence de projet. À partir des répertoires de projet **AwesomeLibrary.CSharp** et de **AwesomeLibrary.FSharp**, vous pouvez exécuter la commande suivante :

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Les fichiers projet pour **AwesomeLibrary.CSharp** et **AwesomeLibrary.FSharp** référencent désormais **AwesomeLibrary.Core** comme cible de `ProjectReference`.  Pour le vérifier, confirmez la présence des éléments suivants dans les fichiers projet :

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Vous pouvez ajouter manuellement cette section à chaque fichier projet si vous préférez ne pas utiliser l’interface CLI .NET Core.

### <a name="structuring-a-solution"></a>Structurer une solution

Un autre aspect important des solutions à projets multiples est la mise en place d’une bonne structure de projet globale. Vous pouvez organiser le code comme vous le souhaitez, et tant que vous liez chaque projet à votre fichier solution avec `dotnet sln add`, vous pouvez exécuter `dotnet restore` et `dotnet build` au niveau de la solution.
