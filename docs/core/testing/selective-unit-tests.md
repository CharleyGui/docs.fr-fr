---
title: Exécution de tests unitaires sélectifs
description: Guide pratique pour utiliser une expression de filtre permettant d’exécuter des tests unitaires sélectifs avec la commande dotnet test dans .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624915"
---
# <a name="running-selective-unit-tests"></a>Exécution de tests unitaires sélectifs

La commande `dotnet test` dans .NET Core vous permet d’utiliser une expression de filtre pour exécuter des tests unitaires sélectifs. Cet article montre comment filtrer les tests exécutés. Les exemples suivants utilisent `dotnet test`. Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.

## <a name="character-escaping"></a>Échappement de caractères

L’utilisation de filtres qui incluent un point d’exclamation ( ! `*nix` ) sur requiert l' `!` échappement, car est réservé. Par exemple, ce filtre ignore tous les tests si l’espace de noms `dotnet test --filter FullyQualifiedName\!~IntegrationTests`contient IntegrationTests :.
Notez la barre oblique inverse qui précède le point d’exclamation.

Pour `FullyQualifiedName` les valeurs qui incluent une virgule pour les paramètres de type générique, échappez la virgule avec `%2C`. Par exemple :

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a>MSTest

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Résultats |
| ---------- | ------ |
| `dotnet test --filter Method` | Exécute les tests dont `FullyQualifiedName` contient `Method`. Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Exécute les tests dont le nom contient `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1`.<br>**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Exécute les tests qui sont annotés avec `[Priority(2)]`.<br>

**Utilisation des opérateurs conditionnels | et &amp;**

| Expression | Résultats |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1. |

## <a name="xunit"></a>xUnit

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| Expression | Résultats |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Exécute les tests dont le nom d’affichage contient `TestClass1`. |

Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.

| Expression | Résultats |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Exécute les tests dont `FullyQualifiedName` contient `XUnit`.  Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Exécute les tests qui ont `[Trait("Category", "CategoryA")]`. |

**Utilisation des opérateurs conditionnels | et &amp;**

| Expression | Résultats |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Exécute les tests qui ont un `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` est 1. |

## <a name="nunit"></a>NUnit

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Résultats |
| ---------- | ------ |
| `dotnet test --filter Method` | Exécute les tests dont `FullyQualifiedName` contient `Method`. Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Exécute les tests dont le nom contient `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Exécute les tests qui sont annotés avec `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Exécute les tests qui sont annotés avec `[Priority(2)]`.<br>

**Utilisation des opérateurs conditionnels | et &amp;**

| Expression | Résultats |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1. |

Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).
