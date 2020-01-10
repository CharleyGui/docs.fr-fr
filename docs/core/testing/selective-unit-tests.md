---
title: Exécution de tests unitaires sélectifs
description: Guide pratique pour utiliser une expression de filtre permettant d’exécuter des tests unitaires sélectifs avec la commande dotnet test dans .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715457"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="48f4d-103">Exécution de tests unitaires sélectifs</span><span class="sxs-lookup"><span data-stu-id="48f4d-103">Running selective unit tests</span></span>

<span data-ttu-id="48f4d-104">La commande `dotnet test` dans .NET Core vous permet d’utiliser une expression de filtre pour exécuter des tests unitaires sélectifs.</span><span class="sxs-lookup"><span data-stu-id="48f4d-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="48f4d-105">Cet article montre comment filtrer les tests exécutés.</span><span class="sxs-lookup"><span data-stu-id="48f4d-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="48f4d-106">Les exemples suivants utilisent `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="48f4d-107">Si vous utilisez `vstest.console.exe`, remplacez `--filter` par `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="48f4d-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="48f4d-108">MSTest</span></span>

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

| <span data-ttu-id="48f4d-109">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-109">Expression</span></span> | <span data-ttu-id="48f4d-110">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="48f4d-111">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="48f4d-112">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="48f4d-113">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="48f4d-114">Exécute les tests qui sont dans la classe `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="48f4d-115">**Remarque :** La valeur `ClassName` doit avoir un espace de noms, donc `ClassName=UnitTest1` ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="48f4d-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="48f4d-116">Exécute tous les tests sauf `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="48f4d-117">Exécute les tests qui sont annotés avec `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="48f4d-118">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="48f4d-119">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="48f4d-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="48f4d-120">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-120">Expression</span></span> | <span data-ttu-id="48f4d-121">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="48f4d-122">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="48f4d-123">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="48f4d-124">Exécute les tests qui ont `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="48f4d-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="48f4d-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="48f4d-125">xUnit</span></span>

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

| <span data-ttu-id="48f4d-126">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-126">Expression</span></span> | <span data-ttu-id="48f4d-127">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="48f4d-128">Exécute uniquement un test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="48f4d-129">Exécute tous les tests sauf `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="48f4d-130">Exécute les tests dont le nom d’affichage contient `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="48f4d-131">Dans l’exemple de code, les caractéristiques définies avec les clés `Category` et `Priority` peuvent être utilisées pour filtrer.</span><span class="sxs-lookup"><span data-stu-id="48f4d-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="48f4d-132">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-132">Expression</span></span> | <span data-ttu-id="48f4d-133">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="48f4d-134">Exécute les tests dont `FullyQualifiedName` contient `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="48f4d-135">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="48f4d-136">Exécute les tests qui ont `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="48f4d-137">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="48f4d-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="48f4d-138">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-138">Expression</span></span> | <span data-ttu-id="48f4d-139">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="48f4d-140">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **ou** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="48f4d-141">Exécute les tests qui ont `TestClass1` dans `FullyQualifiedName` **et** `Category` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="48f4d-142">Exécute les tests qui ont `FullyQualifiedName` contenant `TestClass1` **et** `Category` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="48f4d-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="48f4d-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="48f4d-143">NUnit</span></span>

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

| <span data-ttu-id="48f4d-144">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-144">Expression</span></span> | <span data-ttu-id="48f4d-145">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="48f4d-146">Exécute les tests dont `FullyQualifiedName` contient `Method`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="48f4d-147">Disponible dans `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="48f4d-148">Exécute les tests dont le nom contient `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="48f4d-149">Exécute les tests qui sont dans la classe `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="48f4d-150">Exécute tous les tests sauf `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="48f4d-151">Exécute les tests qui sont annotés avec `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="48f4d-152">Exécute les tests qui sont annotés avec `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="48f4d-153">**Utilisation des opérateurs conditionnels | et &amp;**</span><span class="sxs-lookup"><span data-stu-id="48f4d-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="48f4d-154">Expression</span><span class="sxs-lookup"><span data-stu-id="48f4d-154">Expression</span></span> | <span data-ttu-id="48f4d-155">Résultat</span><span class="sxs-lookup"><span data-stu-id="48f4d-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="48f4d-156">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **ou** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="48f4d-157">Exécute les tests qui ont `UnitTest1` dans `FullyQualifiedName` **et** `TestCategory` est `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="48f4d-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="48f4d-158">Exécute les tests qui ont `FullyQualifiedName` contenant `UnitTest1` **et** `TestCategory` est `CategoryA` **ou** `Priority` a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="48f4d-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
