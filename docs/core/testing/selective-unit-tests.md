---
title: Exécution de tests unitaires sélectifs
description: Guide pratique pour utiliser une expression de filtre permettant d’exécuter des tests unitaires sélectifs avec la commande dotnet test dans .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543506"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="99f8b-103">Exécution de tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="99f8b-103">Running selective unit tests</span></span>

<span data-ttu-id="99f8b-104">La commande `dotnet test` dans .NET Core vous permet d’utiliser une expression de filtre pour exécuter des tests unitaires sélectifs.</span><span class="sxs-lookup"><span data-stu-id="99f8b-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="99f8b-105">Cet article montre comment filtrer les tests exécutés.</span><span class="sxs-lookup"><span data-stu-id="99f8b-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="99f8b-106">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="99f8b-107">Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="99f8b-108">L’utilisation de filtres qui incluent un point d’exclamation ( !) sur `*nix` requiert l’échappement, car `!` est réservé.</span><span class="sxs-lookup"><span data-stu-id="99f8b-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="99f8b-109">Par exemple, ce filtre ignore tous les tests si l’espace de noms contient IntegrationTests : `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="99f8b-110">Notez la barre oblique inverse qui précède le point d’exclamation.</span><span class="sxs-lookup"><span data-stu-id="99f8b-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="99f8b-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="99f8b-111">MSTest</span></span>

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

| <span data-ttu-id="99f8b-112">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-112">Expression</span></span> | <span data-ttu-id="99f8b-113">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="99f8b-114">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="99f8b-115">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="99f8b-116">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="99f8b-117">Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="99f8b-118">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="99f8b-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="99f8b-119">Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="99f8b-120">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="99f8b-121">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="99f8b-122">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="99f8b-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="99f8b-123">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-123">Expression</span></span> | <span data-ttu-id="99f8b-124">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="99f8b-125">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="99f8b-126">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="99f8b-127">Exécute les tests qui ont `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="99f8b-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="99f8b-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="99f8b-128">xUnit</span></span>

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

| <span data-ttu-id="99f8b-129">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-129">Expression</span></span> | <span data-ttu-id="99f8b-130">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="99f8b-131">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="99f8b-132">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="99f8b-133">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="99f8b-134">Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="99f8b-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="99f8b-135">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-135">Expression</span></span> | <span data-ttu-id="99f8b-136">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="99f8b-137">Exécute les tests dont `FullyQualifiedName` contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="99f8b-138">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="99f8b-139">Exécute les tests qui ont `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="99f8b-140">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="99f8b-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="99f8b-141">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-141">Expression</span></span> | <span data-ttu-id="99f8b-142">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="99f8b-143">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="99f8b-144">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="99f8b-145">Exécute les tests qui ont `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="99f8b-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="99f8b-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="99f8b-146">NUnit</span></span>

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

| <span data-ttu-id="99f8b-147">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-147">Expression</span></span> | <span data-ttu-id="99f8b-148">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="99f8b-149">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="99f8b-150">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="99f8b-151">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="99f8b-152">Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="99f8b-153">Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="99f8b-154">Exécute les tests qui sont annotés avec `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="99f8b-155">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="99f8b-156">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="99f8b-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="99f8b-157">Expression</span><span class="sxs-lookup"><span data-stu-id="99f8b-157">Expression</span></span> | <span data-ttu-id="99f8b-158">Résultats</span><span class="sxs-lookup"><span data-stu-id="99f8b-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="99f8b-159">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="99f8b-160">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="99f8b-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="99f8b-161">Exécute les tests qui ont `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="99f8b-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
