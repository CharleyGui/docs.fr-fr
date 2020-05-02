---
title: Exécution de tests unitaires sélectifs
description: Guide pratique pour utiliser une expression de filtre permettant d’exécuter des tests unitaires sélectifs avec la commande dotnet test dans .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728178"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="51877-103">Exécuter des tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="51877-103">Run selective unit tests</span></span>

<span data-ttu-id="51877-104">La commande `dotnet test` dans .NET Core vous permet d’utiliser une expression de filtre pour exécuter des tests unitaires sélectifs.</span><span class="sxs-lookup"><span data-stu-id="51877-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="51877-105">Cet article montre comment filtrer les tests qui sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="51877-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="51877-106">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="51877-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="51877-107">Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="51877-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="51877-108">Échappement de caractères</span><span class="sxs-lookup"><span data-stu-id="51877-108">Character escaping</span></span>

<span data-ttu-id="51877-109">L’utilisation de filtres qui incluent un point d’exclamation ( ! `*nix` ) sur requiert l' `!` échappement, car est réservé.</span><span class="sxs-lookup"><span data-stu-id="51877-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="51877-110">Par exemple, ce filtre ignore tous les tests si l’espace de noms `dotnet test --filter FullyQualifiedName\!~IntegrationTests`contient IntegrationTests :.</span><span class="sxs-lookup"><span data-stu-id="51877-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="51877-111">Notez la barre oblique inverse qui précède le point d’exclamation.</span><span class="sxs-lookup"><span data-stu-id="51877-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="51877-112">Pour `FullyQualifiedName` les valeurs qui incluent une virgule pour les paramètres de type générique, échappez la virgule avec `%2C`.</span><span class="sxs-lookup"><span data-stu-id="51877-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="51877-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="51877-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="51877-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="51877-114">MSTest</span></span>

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

| <span data-ttu-id="51877-115">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-115">Expression</span></span> | <span data-ttu-id="51877-116">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="51877-117">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="51877-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="51877-118">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51877-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="51877-119">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51877-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="51877-120">Exécute les tests qui sont dans `MSTestNamespace.UnitTest1`la classe.</span><span class="sxs-lookup"><span data-stu-id="51877-120">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="51877-121">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="51877-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="51877-122">Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51877-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="51877-123">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="51877-123">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="51877-124">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="51877-124">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="51877-125">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="51877-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51877-126">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-126">Expression</span></span> | <span data-ttu-id="51877-127">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="51877-128">Exécute les tests qui `UnitTest1` ont `FullyQualifiedName` dans **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-128">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="51877-129">Exécute les tests qui `UnitTest1` ont `FullyQualifiedName` dans **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-129">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51877-130">Exécute les tests qui contiennent `FullyQualifiedName` soit `UnitTest1` **et** `TestCategory` a `CategoryA` la valeur **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="51877-130">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="51877-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="51877-131">xUnit</span></span>

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

| <span data-ttu-id="51877-132">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-132">Expression</span></span> | <span data-ttu-id="51877-133">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="51877-134">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="51877-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="51877-135">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="51877-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="51877-136">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="51877-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="51877-137">Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="51877-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="51877-138">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-138">Expression</span></span> | <span data-ttu-id="51877-139">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="51877-140">Exécute les tests dont `FullyQualifiedName` contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="51877-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="51877-141">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51877-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="51877-142">Exécute les tests qui `[Trait("Category", "CategoryA")]`ont.</span><span class="sxs-lookup"><span data-stu-id="51877-142">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="51877-143">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="51877-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51877-144">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-144">Expression</span></span> | <span data-ttu-id="51877-145">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="51877-146">Exécute les tests qui `TestClass1` ont `FullyQualifiedName` dans **ou** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-146">Runs tests that have `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="51877-147">Exécute les tests qui `TestClass1` ont `FullyQualifiedName` dans **et** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-147">Runs tests that have `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51877-148">Exécute les tests qui contiennent `FullyQualifiedName` soit `TestClass1` **et** `Category` a `CategoryA` la valeur **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="51877-148">Runs tests that have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="51877-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="51877-149">NUnit</span></span>

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

| <span data-ttu-id="51877-150">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-150">Expression</span></span> | <span data-ttu-id="51877-151">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="51877-152">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="51877-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="51877-153">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51877-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="51877-154">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51877-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="51877-155">Exécute les tests qui sont dans `NUnitNamespace.UnitTest1`la classe.</span><span class="sxs-lookup"><span data-stu-id="51877-155">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="51877-156">Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51877-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="51877-157">Exécute les tests qui sont annotés avec `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="51877-157">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="51877-158">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="51877-158">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="51877-159">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="51877-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51877-160">Expression</span><span class="sxs-lookup"><span data-stu-id="51877-160">Expression</span></span> | <span data-ttu-id="51877-161">Résultats</span><span class="sxs-lookup"><span data-stu-id="51877-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="51877-162">Exécute les tests qui `UnitTest1` ont `FullyQualifiedName` dans **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-162">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="51877-163">Exécute les tests qui `UnitTest1` ont `FullyQualifiedName` dans **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51877-163">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51877-164">Exécute les tests qui contiennent `FullyQualifiedName` soit `UnitTest1` **et** `TestCategory` a `CategoryA` la valeur **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="51877-164">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="51877-165">Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="51877-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
