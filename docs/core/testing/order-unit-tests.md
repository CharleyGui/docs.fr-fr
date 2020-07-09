---
title: Trier les tests unitaires
description: Découvrez comment commander des tests unitaires avec .NET Core.
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: eb426b790e0623b0cf233a763e93d2bd501b8034
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100819"
---
# <a name="order-unit-tests"></a>Trier les tests unitaires

Parfois, vous souhaiterez peut-être que les tests unitaires s’exécutent dans un ordre spécifique. Dans l’idéal, l’ordre dans lequel les tests unitaires s’exécutent _n’a pas_ d’importance, et il est [recommandé](unit-testing-best-practices.md) d’éviter de classer les tests unitaires. Quoi qu’il en soit, il peut être nécessaire de le faire. Dans ce cas, cet article montre comment ordonner des séries de tests.

Si vous préférez parcourir le code source, consultez le référentiel d’exemples [Order .net Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) .

> [!TIP]
> En plus des fonctionnalités de classement décrites dans cet article, envisagez de [créer des sélections personnalisées avec Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) comme alternative.

:::zone pivot="mstest"

## <a name="order-alphabetically"></a>Classer par ordre alphabétique

Avec MSTest, les tests sont automatiquement classés par nom de test.

> [!NOTE]
> Un test nommé `Test14` s’exécutera avant `Test2` même si le nombre `2` est inférieur à `14` . En effet, le classement des noms de tests utilise le nom de texte du test.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

L’infrastructure de test xUnit permet une plus grande granularité et un meilleur contrôle de l’ordre d’exécution des tests. Vous implémentez `ITestCaseOrderer` les `ITestCollectionOrderer` interfaces et pour contrôler l’ordre des cas de test pour une classe, ou les collections de test.

## <a name="order-by-test-case-alphabetically"></a>Classer par cas de test par ordre alphabétique

Pour classer les cas de test par leur nom de méthode, implémentez le `ITestCaseOrderer` et fournissez un mécanisme de tri.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

Ensuite, dans une classe de test, vous définissez l’ordre des cas de test avec `TestCaseOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a>Classer par collection par ordre alphabétique

Pour classer les collections de test par leur nom d’affichage, vous devez implémenter le `ITestCollectionOrderer` et fournir un mécanisme de commande.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

Étant donné que les collections de tests peuvent s’exécuter en parallèle, vous devez désactiver explicitement la parallélisation de test des collections avec le `CollectionBehaviorAttribute` . Spécifiez ensuite l’implémentation du `TestCollectionOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a>Classer par attribut personnalisé

Pour classer les tests xUnit avec des attributs personnalisés, vous devez d’abord utiliser un attribut. Définissez un `TestPriorityAttribute` comme suit :

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

Examinez ensuite l' `PriorityOrderer` implémentation suivante de l' `ITestCaseOrderer` interface.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

Ensuite, dans une classe de test, vous définissez l’ordre des cas de test avec le `TestCaseOrdererAttribute` sur `PriorityOrderer` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a>Classer par priorité

Pour trier les tests explicitement, NUnit fournit un [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) . Les tests avec cet attribut sont démarrés avant les tests sans. La valeur d’ordre est utilisée pour déterminer l’ordre d’exécution des tests unitaires.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Couverture du code de test unitaire](unit-testing-code-coverage.md)
