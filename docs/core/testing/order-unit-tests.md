---
title: Trier les tests unitaires
description: Découvrez comment commander des tests unitaires avec .NET Core.
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: a7b6b66e4cc865d4ec6b7cfc31ac79767935df2f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506381"
---
# <a name="order-unit-tests"></a><span data-ttu-id="22239-103">Trier les tests unitaires</span><span class="sxs-lookup"><span data-stu-id="22239-103">Order unit tests</span></span>

<span data-ttu-id="22239-104">Parfois, vous souhaiterez peut-être que les tests unitaires s’exécutent dans un ordre spécifique.</span><span class="sxs-lookup"><span data-stu-id="22239-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="22239-105">Dans l’idéal, l’ordre dans lequel les tests unitaires s’exécutent _n’a pas_ d’importance, et il est [recommandé](unit-testing-best-practices.md) d’éviter de classer les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="22239-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="22239-106">Quoi qu’il en soit, il peut être nécessaire de le faire.</span><span class="sxs-lookup"><span data-stu-id="22239-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="22239-107">Dans ce cas, cet article montre comment ordonner des séries de tests.</span><span class="sxs-lookup"><span data-stu-id="22239-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="22239-108">Si vous préférez parcourir le code source, consultez le référentiel d’exemples [Order .net Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) .</span><span class="sxs-lookup"><span data-stu-id="22239-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="22239-109">En plus des fonctionnalités de classement décrites dans cet article, envisagez de [créer des sélections personnalisées avec Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) comme alternative.</span><span class="sxs-lookup"><span data-stu-id="22239-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="22239-110">Classer par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="22239-110">Order alphabetically</span></span>

<span data-ttu-id="22239-111">Avec MSTest, les tests sont automatiquement classés par nom de test.</span><span class="sxs-lookup"><span data-stu-id="22239-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="22239-112">Un test nommé `Test14` s’exécutera avant `Test2` même si le nombre  `2` est inférieur à `14` .</span><span class="sxs-lookup"><span data-stu-id="22239-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="22239-113">En effet, le classement des noms de tests utilise le nom de texte du test.</span><span class="sxs-lookup"><span data-stu-id="22239-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="22239-114">L’infrastructure de test xUnit permet une plus grande granularité et un meilleur contrôle de l’ordre d’exécution des tests.</span><span class="sxs-lookup"><span data-stu-id="22239-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="22239-115">Vous implémentez `ITestCaseOrderer` les `ITestCollectionOrderer` interfaces et pour contrôler l’ordre des cas de test pour une classe, ou les collections de test.</span><span class="sxs-lookup"><span data-stu-id="22239-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="22239-116">Classer par cas de test par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="22239-116">Order by test case alphabetically</span></span>

<span data-ttu-id="22239-117">Pour classer les cas de test par leur nom de méthode, implémentez le `ITestCaseOrderer` et fournissez un mécanisme de tri.</span><span class="sxs-lookup"><span data-stu-id="22239-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="22239-118">Ensuite, dans une classe de test, vous définissez l’ordre des cas de test avec `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="22239-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="22239-119">Classer par collection par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="22239-119">Order by collection alphabetically</span></span>

<span data-ttu-id="22239-120">Pour classer les collections de test par leur nom d’affichage, vous devez implémenter le `ITestCollectionOrderer` et fournir un mécanisme de commande.</span><span class="sxs-lookup"><span data-stu-id="22239-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="22239-121">Étant donné que les collections de tests peuvent s’exécuter en parallèle, vous devez désactiver explicitement la parallélisation de test des collections avec le `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="22239-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="22239-122">Spécifiez ensuite l’implémentation du `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="22239-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="22239-123">Classer par attribut personnalisé</span><span class="sxs-lookup"><span data-stu-id="22239-123">Order by custom attribute</span></span>

<span data-ttu-id="22239-124">Pour classer les tests xUnit avec des attributs personnalisés, vous devez d’abord utiliser un attribut.</span><span class="sxs-lookup"><span data-stu-id="22239-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="22239-125">Définissez un `TestPriorityAttribute` comme suit :</span><span class="sxs-lookup"><span data-stu-id="22239-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="22239-126">Examinez ensuite l' `PriorityOrderer` implémentation suivante de l' `ITestCaseOrderer` interface.</span><span class="sxs-lookup"><span data-stu-id="22239-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="22239-127">Ensuite, dans une classe de test, vous définissez l’ordre des cas de test avec le `TestCaseOrdererAttribute` sur `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="22239-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="22239-128">Classer par priorité</span><span class="sxs-lookup"><span data-stu-id="22239-128">Order by priority</span></span>

<span data-ttu-id="22239-129">Pour trier les tests explicitement, NUnit fournit un [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="22239-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="22239-130">Les tests avec cet attribut sont démarrés avant les tests sans.</span><span class="sxs-lookup"><span data-stu-id="22239-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="22239-131">La valeur d’ordre est utilisée pour déterminer l’ordre d’exécution des tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="22239-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="22239-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="22239-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="22239-133">Couverture du code de test unitaire</span><span class="sxs-lookup"><span data-stu-id="22239-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
