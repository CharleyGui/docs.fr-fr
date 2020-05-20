---
title: Exécuter des tests unitaires sélectifs
description: Guide pratique pour utiliser une expression de filtre permettant d’exécuter des tests unitaires sélectifs avec la commande dotnet test dans .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702982"
---
# <a name="run-selective-unit-tests"></a>Exécuter des tests unitaires sélectifs

Avec la [`dotnet test`](../tools/dotnet-test.md) commande dans .net Core, vous pouvez utiliser une expression de filtre pour exécuter des tests sélectifs. Cet article montre comment filtrer les tests qui sont exécutés. Les exemples suivants utilisent `dotnet test`. Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.

## <a name="character-escaping"></a>Échappement de caractères

L’utilisation de filtres qui incluent un point `!` d’exclamation sur `*nix` requiert l’échappement `!` , car est réservé. Par exemple, ce filtre ignore tous les tests si l’espace de noms contient IntegrationTests :

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> La barre oblique inverse précède le point d’exclamation pour indiquer qu’il s’agit d’un caractère d’échappement `\!` .

Pour `FullyQualifiedName` les valeurs qui incluent une virgule pour les paramètres de type générique, échappez la virgule avec `%2C` . Par exemple :

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Résultats |
|--|--|
| `dotnet test --filter Method` | Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `Method`. Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Exécute les tests dont le nom contient `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1` .<br>**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Exécute les tests qui sont annotés avec `[Priority(2)]` . |

Exemples utilisant les opérateurs conditionnels `|` et `&` :

Pour exécuter les tests qui ont `UnitTest1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> est `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Pour exécuter les tests qui ont `UnitTest1` dans <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Pour exécuter des tests qui contiennent <xref:System.Reflection.Module.FullyQualifiedName> l' `UnitTest1` **and** un <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` **ou** dont la priorité est <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| Expression | Résultats |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Exécute les tests dont le nom d’affichage contient `TestClass1`. |

Dans l’exemple de code, les caractéristiques définies avec les clés `"Category"` et `"Priority"` peuvent être utilisées pour filtrer.

| Expression | Résultats |
|--|--|
| `dotnet test --filter XUnit` | Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `XUnit`.  Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Exécute les tests qui ont `[Trait("Category", "CategoryA")]` . |

Exemples utilisant les opérateurs conditionnels `|` et `&` :

Pour exécuter des tests qui ont `TestClass1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** ont un `Trait` avec une clé `"Category"` et une valeur de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

Pour exécuter les tests qui ont `TestClass1` dans leurs <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un `Trait` avec une clé `"Category"` et la valeur de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

Pour exécuter des tests qui contiennent <xref:System.Reflection.Module.FullyQualifiedName> soit `TestClass1` **et** ont un `Trait` avec la clé `"Category"` et la valeur de, `"CategoryA"` **soit** un `Trait` avec une clé `"Priority"` et une valeur de `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Résultats |
|--|--|
| `dotnet test --filter Method` | Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `Method`. Disponible dans `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Exécute les tests dont le nom contient `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1` . |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Exécute les tests qui sont annotés avec `[Category("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Exécute les tests qui sont annotés avec `[Priority(2)]` . |

Exemples utilisant les opérateurs conditionnels `|` et `&` :

Pour exécuter des tests qui ont `UnitTest1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** ont un `Category` de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Pour exécuter les tests qui ont `UnitTest1` dans <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un `Category` de `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Pour exécuter des tests qui ont un <xref:System.Reflection.Module.FullyQualifiedName> conteneur `UnitTest1` **et** ont un `Category` de `"CategoryA"` **ou** un `Property` avec un `"Priority"` de `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>Voir aussi

- [dotnet test](../tools/dotnet-test.md)
- [test dotnet--filtre](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Trier les tests unitaires](order-unit-tests.md)
