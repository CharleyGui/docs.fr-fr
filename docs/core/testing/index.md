---
title: Test dans .NET
description: Cet article fournit une brève présentation des concepts de test, de la terminologie et des outils de test dans .NET.
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 36e88cc059447a98931593e0535c70cbc92a2cf4
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223469"
---
# <a name="testing-in-net"></a>Test dans .NET

Cet article présente le concept de test et illustre la manière dont différents genres de tests peuvent être utilisés pour valider le code. Plusieurs outils sont disponibles pour tester des applications .NET, telles que l' [interface de commande CLI .net](#net-cli) ou les [environnements de développement intégré (IDE)](#ide).

## <a name="test-types"></a>Types de test

Le fait de disposer de tests automatisés est un excellent moyen de s’assurer que le code d’application fait ce que les auteurs l’envisagent de faire. Cet article couvre les tests unitaires, les tests d’intégration et les tests de charge.

### <a name="unit-tests"></a>Tests unitaires

Un *test unitaire* est un test qui exerce des composants logiciels individuels ou des méthodes, également appelées « unités de travail ». Les tests unitaires doivent uniquement tester le code dans le contrôle du développeur. Ils ne testent pas les problèmes d’infrastructure. Les problèmes d’infrastructure incluent l’interaction avec les bases de données, les systèmes de fichiers et les ressources réseau.

Pour plus d’informations sur la création de tests unitaires, consultez [outils de test](#testing-tools).

### <a name="integration-tests"></a>Tests d’intégration

Un *test d’intégration* diffère d’un test unitaire dans la mesure où il exerce deux ou plusieurs composants logiciels pour fonctionner ensemble, également appelé « intégration ». Ces tests fonctionnent sur un spectre plus large du système testé, tandis que les tests unitaires se concentrent sur des composants individuels. Souvent, les tests d’intégration incluent des problèmes d’infrastructure.

### <a name="load-tests"></a>Tests de charge

Un *test de charge* a pour but de déterminer si un système peut gérer une charge spécifiée, par exemple, le nombre d’utilisateurs simultanés utilisant une application et la capacité de l’application à gérer les interactions de façon réactive. Pour plus d’informations sur le test de charge des applications Web, consultez [ASP.net core le test de charge ou de stress](/aspnet/core/test/load-tests).

## <a name="test-considerations"></a>Considérations relatives aux tests

Gardez à l’esprit qu’il existe des [pratiques recommandées](unit-testing-best-practices.md) pour l’écriture des tests. Par exemple, le [développement piloté par les tests (TDD)](https://deviq.com/test-driven-development) est le moment où un test unitaire est écrit avant le code qu’il doit vérifier. TDD est semblable à la création d’un plan pour un livre avant de l’écrire. Il est conçu pour aider les développeurs à écrire du code plus simple, plus lisible et plus efficace.

## <a name="testing-tools"></a>Outils de test

.Net est une plateforme de développement multilingue, et vous pouvez écrire différents types de test pour [C#](../../csharp/index.yml), [F #](../../fsharp/index.yml)et [Visual Basic](../../visual-basic/index.yml). Pour chacune de ces langues, vous pouvez choisir entre plusieurs infrastructures de test.

### <a name="xunit"></a>xUnit

[xUnit](https://xunit.net) est un outil de test d’unités libre, open source et axé sur la communauté pour .net. Écrit par l’inventeur d’origine de NUnit v2, xUnit.net est la technologie la plus récente pour le test unitaire des applications .NET. xUnit.net fonctionne avec resharper, CodeRush, TestDriven.NET et [Xamarin](/apps/xamarin). Il s’agit d’un projet de [.net Foundation](https://dotnetfoundation.org) qui fonctionne dans le cadre de son code de réalisation.

Pour plus d’informations, consultez les ressources suivantes :

- [Tests unitaires avec C #](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec F #](unit-testing-fsharp-with-dotnet-test.md)
- [Tests unitaires avec Visual Basic](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a>NUnit

[Nunit](https://nunit.org) est une infrastructure de tests unitaires pour tous les langages .net. Initialement porté à partir de JUnit, la version de production actuelle a été réécrite avec de nombreuses nouvelles fonctionnalités et la prise en charge d’une large gamme de plateformes .NET. Il s’agit d’un projet de [.net Foundation](https://dotnetfoundation.org).

Pour plus d’informations, consultez les ressources suivantes :

- [Tests unitaires avec C #](unit-testing-with-nunit.md)
- [Tests unitaires avec F #](unit-testing-fsharp-with-nunit.md)
- [Tests unitaires avec Visual Basic](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a>MSTest

[MSTest](https://github.com/Microsoft/testfx-docs) est l’infrastructure de test Microsoft pour tous les langages .net. Il est extensible et fonctionne avec la CLI .NET et Visual Studio. Pour plus d’informations, consultez les ressources suivantes :

- [Tests unitaires avec C #](unit-testing-with-mstest.md)
- [Tests unitaires avec F #](unit-testing-fsharp-with-mstest.md)
- [Tests unitaires avec Visual Basic](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a>CLI .NET

Vous pouvez exécuter des tests unitaires de solutions à partir de l' [interface CLI .net](../tools/index.md), à l’aide de la commande [dotnet test](../tools/dotnet-test.md) . L’interface CLI .NET expose une majorité des fonctionnalités que les [environnements de développement intégré (IDE)](#ide) mettent à disposition via les interfaces utilisateur. L’interface CLI .NET est multiplateforme et peut être utilisée dans le cadre des pipelines d’intégration et de livraison continus. L’interface CLI .NET est utilisée avec les processus scriptés pour automatiser les tâches courantes.

### <a name="ide"></a>IDE

Que vous utilisiez Visual Studio, Visual Studio pour Mac ou Visual Studio Code, il existe des interfaces utilisateur graphiques pour la fonctionnalité de test. D’autres fonctionnalités sont disponibles pour les IDE que l’interface CLI, par exemple [Live Unit testing](/visualstudio/test/live-unit-testing). Pour plus d’informations, consultez [inclure et exclure des tests avec Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations, consultez les articles suivants :

- [Meilleures pratiques en matière de tests unitaires avec .NET](unit-testing-best-practices.md)
- [Tests d’intégration dans ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [Exécution de tests unitaires sélectifs](selective-unit-tests.md)
- [Utiliser la couverture du code pour les tests unitaires](unit-testing-code-coverage.md)
