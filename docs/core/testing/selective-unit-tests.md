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
# <a name="running-selective-unit-tests"></a><span data-ttu-id="d25e2-103">Exécution de tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="d25e2-103">Running selective unit tests</span></span>

<span data-ttu-id="d25e2-104">La commande `dotnet test` dans .NET Core vous permet d’utiliser une expression de filtre pour exécuter des tests unitaires sélectifs.</span><span class="sxs-lookup"><span data-stu-id="d25e2-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="d25e2-105">Cet article montre comment filtrer les tests exécutés.</span><span class="sxs-lookup"><span data-stu-id="d25e2-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="d25e2-106">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="d25e2-107">Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="d25e2-108">Échappement de caractères</span><span class="sxs-lookup"><span data-stu-id="d25e2-108">Character escaping</span></span>

<span data-ttu-id="d25e2-109">L’utilisation de filtres qui incluent un point d’exclamation ( ! `*nix` ) sur requiert l' `!` échappement, car est réservé.</span><span class="sxs-lookup"><span data-stu-id="d25e2-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="d25e2-110">Par exemple, ce filtre ignore tous les tests si l’espace de noms `dotnet test --filter FullyQualifiedName\!~IntegrationTests`contient IntegrationTests :.</span><span class="sxs-lookup"><span data-stu-id="d25e2-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="d25e2-111">Notez la barre oblique inverse qui précède le point d’exclamation.</span><span class="sxs-lookup"><span data-stu-id="d25e2-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="d25e2-112">Pour `FullyQualifiedName` les valeurs qui incluent une virgule pour les paramètres de type générique, échappez la virgule avec `%2C`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="d25e2-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d25e2-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="d25e2-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="d25e2-114">MSTest</span></span>

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

| <span data-ttu-id="d25e2-115">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-115">Expression</span></span> | <span data-ttu-id="d25e2-116">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="d25e2-117">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="d25e2-118">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="d25e2-119">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="d25e2-120">Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-120">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="d25e2-121">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="d25e2-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="d25e2-122">Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="d25e2-123">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-123">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="d25e2-124">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-124">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="d25e2-125">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="d25e2-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d25e2-126">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-126">Expression</span></span> | <span data-ttu-id="d25e2-127">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="d25e2-128">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-128">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="d25e2-129">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-129">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d25e2-130">Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1.</span><span class="sxs-lookup"><span data-stu-id="d25e2-130">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="d25e2-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="d25e2-131">xUnit</span></span>

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

| <span data-ttu-id="d25e2-132">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-132">Expression</span></span> | <span data-ttu-id="d25e2-133">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="d25e2-134">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="d25e2-135">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="d25e2-136">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="d25e2-137">Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="d25e2-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="d25e2-138">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-138">Expression</span></span> | <span data-ttu-id="d25e2-139">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="d25e2-140">Exécute les tests dont `FullyQualifiedName` contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="d25e2-141">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="d25e2-142">Exécute les tests qui ont `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-142">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="d25e2-143">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="d25e2-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d25e2-144">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-144">Expression</span></span> | <span data-ttu-id="d25e2-145">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="d25e2-146">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-146">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="d25e2-147">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-147">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d25e2-148">Exécute les tests qui ont un `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` est 1.</span><span class="sxs-lookup"><span data-stu-id="d25e2-148">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="d25e2-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="d25e2-149">NUnit</span></span>

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

| <span data-ttu-id="d25e2-150">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-150">Expression</span></span> | <span data-ttu-id="d25e2-151">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="d25e2-152">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="d25e2-153">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="d25e2-154">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="d25e2-155">Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-155">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="d25e2-156">Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="d25e2-157">Exécute les tests qui sont annotés avec `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-157">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="d25e2-158">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-158">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="d25e2-159">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="d25e2-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d25e2-160">Expression</span><span class="sxs-lookup"><span data-stu-id="d25e2-160">Expression</span></span> | <span data-ttu-id="d25e2-161">Résultats</span><span class="sxs-lookup"><span data-stu-id="d25e2-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="d25e2-162">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-162">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="d25e2-163">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="d25e2-163">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d25e2-164">Exécute les tests qui ont un `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` est 1.</span><span class="sxs-lookup"><span data-stu-id="d25e2-164">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="d25e2-165">Pour plus d’informations, consultez [TestCase Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="d25e2-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
