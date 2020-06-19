---
title: Utiliser la couverture du code pour les tests unitaires
description: Découvrez comment utiliser les fonctionnalités de couverture du code pour les tests unitaires .NET.
author: IEvangelist
ms.author: dapine
ms.date: 06/16/2020
ms.openlocfilehash: 47f10ae367f511d5d02d32bfcb35bf4775a3e946
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990278"
---
# <a name="use-code-coverage-for-unit-testing"></a>Utiliser la couverture du code pour les tests unitaires

Les tests unitaires permettent de garantir des fonctionnalités et de fournir un moyen de vérification des efforts de refactorisation. La couverture du code est une mesure de la quantité de code exécutée par les tests unitaires : lignes, branches ou méthodes. Par exemple, si vous avez une application simple avec deux branches conditionnelles de code (_branche a_et _branche b_), un test unitaire qui vérifie _la branche conditionnelle a_ indiquera la couverture du code de branche de 50%.

Cet article traite de l’utilisation de la couverture du code pour les tests unitaires avec coverlet et la génération de rapports à l’aide de ReportGenerator. Bien que cet article se concentre sur C# et xUnit comme Framework de test, MSTest et NUnit fonctionnent également. Coverlet est un [projet open source sur GitHub](https://github.com/coverlet-coverage/coverlet) qui fournit une infrastructure de couverture de code multiplateforme pour C#. [Coverlet](https://dotnetfoundation.org/projects/coverlet) fait partie de .net Foundation. Coverlet collecte les données de série de tests de couverture cobertura, qui sont utilisées pour la génération de rapports.

En outre, cet article explique comment utiliser les informations de couverture du code collectées à partir d’une série de tests coverlet pour générer un rapport. La génération de rapports est possible à l’aide d’un autre [projet open source sur GitHub-ReportGenerator](https://github.com/danielpalme/ReportGenerator). ReportGenerator convertit les rapports de couverture générés par cobertura entre plusieurs autres, en rapports lisibles par les humains dans différents formats.

## <a name="system-under-test"></a>Système testé

Le « système testé » fait référence au code sur lequel vous écrivez des tests unitaires, il peut s’agir d’un objet, d’un service ou tout autre qui expose des fonctionnalités testable. Dans le cadre de cet article, vous allez créer une bibliothèque de classes qui sera le système testé et deux projets de test unitaire correspondants.

### <a name="create-a-class-library"></a>Créer une bibliothèque de classes

À partir d’une invite de commandes dans un nouveau répertoire nommé `UnitTestingCodeCoverage` , créez une bibliothèque de classes .NET standard à l’aide de la [`dotnet new classlib`](../tools/dotnet-new.md#classlib) commande :

```dotnetcli
dotnet new classlib -n Numbers
```

L’extrait de code ci-dessous définit une `PrimeService` classe simple qui fournit des fonctionnalités permettant de vérifier si un nombre est premier. Copiez l’extrait de code ci-dessous et remplacez le contenu du fichier *Class1.cs* qui a été créé automatiquement dans le répertoire *numbers* . Renommez le fichier *Class1.cs* en *PrimeService.cs*.

```csharp
namespace System.Numbers
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            if (candidate < 2)
            {
                return false;
            }

            for (int divisor = 2; divisor <= Math.Sqrt(candidate); ++divisor)
            {
                if (candidate % divisor == 0)
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

> [!TIP]
> Il est intéressant de mentionner que la `Numbers` bibliothèque de classes a été ajoutée intentionnellement à l' `System` espace de noms. Cela permet <xref:System.Math?displayProperty=fullName> à d’être accessible sans `using System;` déclaration d’espace de noms. Pour plus d’informations, consultez [espace de noms (référence C#)](../../csharp/language-reference/keywords/namespace.md).

### <a name="create-test-projects"></a>Créer des projets de test

Créez deux nouveaux modèles de **projet de test xUnit (.net Core)** à partir de la même invite de commandes à l’aide de la [`dotnet new xunit`](../tools/dotnet-new.md#test) commande :

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.Collector
```

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.MSBuild
```

Les deux projets de test xUnit nouvellement créés doivent ajouter une référence de projet de la bibliothèque de classes *numbers* . Cela permet aux projets de test d’accéder au *PrimeService* à des fins de test. À partir de l’invite de commandes, utilisez la [`dotnet add`](../tools/dotnet-add-reference.md) commande :

```dotnetcli
dotnet add XUnit.Coverlet.Collector\XUnit.Coverlet.Collector.csproj reference Numbers\Numbers.csproj
```

```dotnetcli
dotnet add XUnit.Coverlet.MSBuild\XUnit.Coverlet.MSBuild.csproj reference Numbers\Numbers.csproj
```

Le projet *MSBuild* est nommé de manière appropriée, car il dépend du package NuGet [coverlet. MSBuild](https://www.nuget.org/packages/coverlet.msbuild) . Ajoutez cette dépendance de package en exécutant la [`dotnet add package`](../tools/dotnet-add-package.md) commande suivante :

```dotnetcli
cd XUnit.Coverlet.MSBuild && dotnet add package coverlet.msbuild && cd ..
```

La commande précédente a modifié les répertoires avec efficacité pour le projet de test *MSBuild* , puis j’ai ajouté le package NuGet. Une fois cette opération effectuée, les répertoires ont été modifiés pour remonter d’un niveau.

Ouvrez les deux fichiers *UnitTest1.cs* et remplacez leur contenu par l’extrait de code suivant. Renommez les fichiers *UnitTest1.cs* en *PrimeServiceTests.cs*.

```csharp
using System.Numbers;
using Xunit;

namespace XUnit.Coverlet
{
    public class PrimeServiceTests
    {
        readonly PrimeService _primeService;

        public PrimeServiceTests() => _primeService = new PrimeService();

        [
            Theory,
            InlineData(-1), InlineData(0), InlineData(1)
        ]
        public void IsPrime_ValuesLessThan2_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");

        [
            Theory,
            InlineData(2), InlineData(3), InlineData(5), InlineData(7)
        ]
        public void IsPrime_PrimesLessThan10_ReturnTrue(int value) =>
            Assert.True(_primeService.IsPrime(value), $"{value} should be prime");

        [
            Theory,
            InlineData(4), InlineData(6), InlineData(8), InlineData(9)
        ]
        public void IsPrime_NonPrimesLessThan10_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");
    }
}
```

### <a name="create-a-solution"></a>Créer une solution

À partir de l’invite de commandes, créez une nouvelle solution pour encapsuler la bibliothèque de classes et les deux projets de test. À l’aide de la [`dotnet sln`](../tools/dotnet-sln.md) commande :

```dotnetcli
dotnet new sln -n XUnit.Coverage
```

Cela permet de créer un nouveau nom de fichier solution `XUnit.Coverage` dans le répertoire *UnitTestingCodeCoverage* . Ajoutez les projets à la racine de la solution.

## <a name="linux"></a>[Linux](#tab/linux)

```dotnetcli
dotnet sln XUnit.Coverage.sln add **/*.csproj --in-root
```

## <a name="windows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet sln XUnit.Coverage.sln add (ls **/*.csproj) --in-root
```

---

Générez la solution à l’aide de la [`dotnet build`](../tools/dotnet-build.md) commande :

```dotnetcli
dotnet build
```

Si la génération réussit, vous avez créé les trois projets, des projets et des packages référencés de manière appropriée, et mis à jour le code source correctement. C’est terminé !

## <a name="tooling"></a>Outillage

Il existe deux types d’outils de couverture du code :

- **DataCollectors :** DataCollectors surveiller l’exécution des tests et collecter des informations sur les séries de tests. Ils signalent les informations collectées dans divers formats de sortie, tels que XML et JSON. Pour plus d’informations, consultez [votre premier DataCollector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/datacollector.md).
- **Générateurs de rapports :** Utilisez les données collectées à partir des séries de tests pour générer des rapports, souvent sous forme de styles HTML.

Dans cette section, nous allons nous concentrer sur les outils du collecteur de données. Pour utiliser coverlet pour la couverture du code, un projet de test unitaire existant doit avoir les dépendances de package appropriées, ou s’appuyer sur les [Outils globaux .net](../tools/global-tools.md) et le package NuGet [coverlet. console](https://www.nuget.org/packages/coverlet.console) correspondant.

## <a name="integrate-with-net-test"></a>Intégrer avec le test .NET

Le modèle de projet de test xUnit s’intègre déjà à [coverlet. Collector](https://www.nuget.org/packages/coverlet.collector) par défaut.
À partir de l’invite de commandes, remplacez les répertoires par le projet *xUnit. coverlet. Collector* , puis exécutez la [`dotnet test`](../tools/dotnet-test.md) commande :

```dotnetcli
cd XUnit.Coverlet.Collector && dotnet test --collect:"XPlat Code Coverage"
```

> [!NOTE]
> L' `"XPlat Code Coverage"` argument est un nom convivial qui correspond aux collecteurs de données de coverlet. Ce nom est obligatoire, mais ne respecte pas la casse.

Dans le cadre de l' `dotnet test` exécution, un fichier de *coverage.cobertura.xml* résultant est généré dans le répertoire *TestResults* . Le fichier XML contient les résultats. Il s’agit d’une option multiplateforme qui s’appuie sur le CLI .NET Core et il est parfait pour les systèmes de génération où MSBuild n’est pas disponible.

Voici l’exemple *coverage.cobertura.xml* fichier.

```xml
<?xml version="1.0" encoding="utf-8"?>
<coverage line-rate="1" branch-rate="1" version="1.9" timestamp="1592248008"
          lines-covered="12" lines-valid="12" branches-covered="6" branches-valid="6">
  <sources>
    <source>C:\</source>
  </sources>
  <packages>
    <package name="Numbers" line-rate="1" branch-rate="1" complexity="6">
      <classes>
        <class name="Numbers.PrimeService" line-rate="1" branch-rate="1" complexity="6"
               filename="Numbers\PrimeService.cs">
          <methods>
            <method name="IsPrime" signature="(System.Int32)" line-rate="1"
                    branch-rate="1" complexity="6">
              <lines>
                <line number="8" hits="11" branch="False" />
                <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="7" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="10" hits="3" branch="False" />
                <line number="11" hits="3" branch="False" />
                <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="57" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="15" hits="7" branch="False" />
                <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="27" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="17" hits="4" branch="False" />
                <line number="18" hits="4" branch="False" />
                <line number="20" hits="3" branch="False" />
                <line number="21" hits="4" branch="False" />
                <line number="23" hits="11" branch="False" />
              </lines>
            </method>
          </methods>
          <lines>
            <line number="8" hits="11" branch="False" />
            <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="7" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="10" hits="3" branch="False" />
            <line number="11" hits="3" branch="False" />
            <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="57" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="15" hits="7" branch="False" />
            <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="27" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="17" hits="4" branch="False" />
            <line number="18" hits="4" branch="False" />
            <line number="20" hits="3" branch="False" />
            <line number="21" hits="4" branch="False" />
            <line number="23" hits="11" branch="False" />
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
```

> [!TIP]
> Vous pouvez également utiliser le package MSBuild si votre système de génération utilise déjà MSBuild. À partir de l’invite de commandes, remplacez les répertoires par le projet *xUnit. coverlet. MSBuild* , puis exécutez la `dotnet test` commande :
>
> ```dotnetcli
> dotnet test --collect:"XPlat Code Coverage"
> ```
>
> Le fichier *coverage.cobertura.xml* résultant est output.

## <a name="generate-reports"></a>Génération de rapports

Maintenant que vous êtes en mesure de collecter des données à partir des séries de tests unitaires, vous pouvez générer des rapports à l’aide de [ReportGenerator](https://github.com/danielpalme/ReportGenerator). Pour installer le package NuGet [ReportGenerator](https://www.nuget.org/packages/dotnet-reportgenerator-globaltool) en tant qu' [outil Global .net](../tools/global-tools.md), utilisez la [`dotnet tool install`](../tools/dotnet-tool-install.md) commande suivante :

```dotnetcli
dotnet tool install -g dotnet-reportgenerator-globaltool
```

Exécutez l’outil et fournissez les options souhaitées, en fonction du fichier de *coverage.cobertura.xml* de sortie de la série de tests précédente.

```console
reportgenerator
"-reports:Path\To\TestProject\TestResults\{guid}\coverage.cobertura.xml"
"-targetdir:coveragereport"
-reporttypes:Html
```

Après l’exécution de cette commande, un fichier HTML représente le rapport généré.

:::image type="content" source="media/test-report.png" lightbox="media/test-report.png" alt-text="Test unitaire-rapport généré":::

## <a name="see-also"></a>Voir aussi

- [Couverture des tests unitaires Visual Studio](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)
- [Dépôt GitHub-coverlet](https://github.com/coverlet-coverage/coverlet)
- [Dépôt GitHub-ReportGenerator](https://github.com/danielpalme/ReportGenerator)
- [Site du projet ReportGenerator](https://danielpalme.github.io/ReportGenerator)
- [Commande de test CLI .NET Core](../tools/dotnet-test.md)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Bonnes pratiques relatives aux tests unitaires](unit-testing-best-practices.md)
