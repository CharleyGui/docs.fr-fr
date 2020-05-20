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
# <a name="run-selective-unit-tests"></a><span data-ttu-id="646f6-103">Exécuter des tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="646f6-103">Run selective unit tests</span></span>

<span data-ttu-id="646f6-104">Avec la [`dotnet test`](../tools/dotnet-test.md) commande dans .net Core, vous pouvez utiliser une expression de filtre pour exécuter des tests sélectifs.</span><span class="sxs-lookup"><span data-stu-id="646f6-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="646f6-105">Cet article montre comment filtrer les tests qui sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="646f6-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="646f6-106">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="646f6-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="646f6-107">Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="646f6-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="646f6-108">Échappement de caractères</span><span class="sxs-lookup"><span data-stu-id="646f6-108">Character escaping</span></span>

<span data-ttu-id="646f6-109">L’utilisation de filtres qui incluent un point `!` d’exclamation sur `*nix` requiert l’échappement `!` , car est réservé.</span><span class="sxs-lookup"><span data-stu-id="646f6-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="646f6-110">Par exemple, ce filtre ignore tous les tests si l’espace de noms contient IntegrationTests :</span><span class="sxs-lookup"><span data-stu-id="646f6-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="646f6-111">La barre oblique inverse précède le point d’exclamation pour indiquer qu’il s’agit d’un caractère d’échappement `\!` .</span><span class="sxs-lookup"><span data-stu-id="646f6-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="646f6-112">Pour `FullyQualifiedName` les valeurs qui incluent une virgule pour les paramètres de type générique, échappez la virgule avec `%2C` .</span><span class="sxs-lookup"><span data-stu-id="646f6-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="646f6-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="646f6-113">For example:</span></span>

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

| <span data-ttu-id="646f6-114">Expression</span><span class="sxs-lookup"><span data-stu-id="646f6-114">Expression</span></span> | <span data-ttu-id="646f6-115">Résultats</span><span class="sxs-lookup"><span data-stu-id="646f6-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="646f6-116">Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="646f6-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="646f6-117">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="646f6-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="646f6-118">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="646f6-119">Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="646f6-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="646f6-120">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="646f6-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="646f6-121">Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="646f6-122">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="646f6-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="646f6-123">Exécute les tests qui sont annotés avec `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="646f6-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="646f6-124">Exemples utilisant les opérateurs conditionnels `|` et `&` :</span><span class="sxs-lookup"><span data-stu-id="646f6-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="646f6-125">Pour exécuter les tests qui ont `UnitTest1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> est `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="646f6-126">Pour exécuter les tests qui ont `UnitTest1` dans <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="646f6-127">Pour exécuter des tests qui contiennent <xref:System.Reflection.Module.FullyQualifiedName> l' `UnitTest1` **and** un <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> de `"CategoryA"` **ou** dont la priorité est <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> `1` .</span><span class="sxs-lookup"><span data-stu-id="646f6-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

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

| <span data-ttu-id="646f6-128">Expression</span><span class="sxs-lookup"><span data-stu-id="646f6-128">Expression</span></span> | <span data-ttu-id="646f6-129">Résultats</span><span class="sxs-lookup"><span data-stu-id="646f6-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="646f6-130">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="646f6-131">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="646f6-132">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="646f6-133">Dans l’exemple de code, les caractéristiques définies avec les clés `"Category"` et `"Priority"` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="646f6-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="646f6-134">Expression</span><span class="sxs-lookup"><span data-stu-id="646f6-134">Expression</span></span> | <span data-ttu-id="646f6-135">Résultats</span><span class="sxs-lookup"><span data-stu-id="646f6-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="646f6-136">Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="646f6-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="646f6-137">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="646f6-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="646f6-138">Exécute les tests qui ont `[Trait("Category", "CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="646f6-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="646f6-139">Exemples utilisant les opérateurs conditionnels `|` et `&` :</span><span class="sxs-lookup"><span data-stu-id="646f6-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="646f6-140">Pour exécuter des tests qui ont `TestClass1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** ont un `Trait` avec une clé `"Category"` et une valeur de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="646f6-141">Pour exécuter les tests qui ont `TestClass1` dans leurs <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un `Trait` avec une clé `"Category"` et la valeur de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="646f6-142">Pour exécuter des tests qui contiennent <xref:System.Reflection.Module.FullyQualifiedName> soit `TestClass1` **et** ont un `Trait` avec la clé `"Category"` et la valeur de, `"CategoryA"` **soit** un `Trait` avec une clé `"Priority"` et une valeur de `1` .</span><span class="sxs-lookup"><span data-stu-id="646f6-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

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

| <span data-ttu-id="646f6-143">Expression</span><span class="sxs-lookup"><span data-stu-id="646f6-143">Expression</span></span> | <span data-ttu-id="646f6-144">Résultats</span><span class="sxs-lookup"><span data-stu-id="646f6-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="646f6-145">Exécute les tests dont <xref:System.Reflection.Module.FullyQualifiedName> contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="646f6-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="646f6-146">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="646f6-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="646f6-147">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="646f6-148">Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="646f6-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="646f6-149">Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="646f6-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="646f6-150">Exécute les tests qui sont annotés avec `[Category("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="646f6-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="646f6-151">Exécute les tests qui sont annotés avec `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="646f6-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="646f6-152">Exemples utilisant les opérateurs conditionnels `|` et `&` :</span><span class="sxs-lookup"><span data-stu-id="646f6-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="646f6-153">Pour exécuter des tests qui ont `UnitTest1` dans leur <xref:System.Reflection.Module.FullyQualifiedName> **ou** ont un `Category` de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="646f6-154">Pour exécuter les tests qui ont `UnitTest1` dans <xref:System.Reflection.Module.FullyQualifiedName> **et** ont un `Category` de `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="646f6-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="646f6-155">Pour exécuter des tests qui ont un <xref:System.Reflection.Module.FullyQualifiedName> conteneur `UnitTest1` **et** ont un `Category` de `"CategoryA"` **ou** un `Property` avec un `"Priority"` de `1` .</span><span class="sxs-lookup"><span data-stu-id="646f6-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="646f6-156">Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="646f6-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="646f6-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="646f6-157">See also</span></span>

- [<span data-ttu-id="646f6-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="646f6-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="646f6-159">test dotnet--filtre</span><span class="sxs-lookup"><span data-stu-id="646f6-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="646f6-160">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="646f6-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="646f6-161">Trier les tests unitaires</span><span class="sxs-lookup"><span data-stu-id="646f6-161">Order unit tests</span></span>](order-unit-tests.md)
