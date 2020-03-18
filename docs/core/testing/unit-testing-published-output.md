---
title: Tester la sortie publiée avec dotnet vstest
description: Découvrez comment exécuter des tests sur des bibliothèques publiées plutôt que sur le code source avec la commande dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714267"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Tester la sortie publiée avec dotnet vstest

Vous pouvez exécuter des tests sur la sortie déjà publiée à l’aide de la commande `dotnet vstest`. Cela s’applique aux tests sur xUnit, MSTest et NUnit. Recherchez simplement le fichier DLL qui faisait partie de votre sortie publiée et exécutez :

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

où `<MyPublishedTests>` est le nom de votre projet de test publié.

## <a name="example"></a> Exemple

Les commandes ci-dessous montrent des tests en cours d’exécution sur une DLL publiée.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Remarque : Si votre application `netcoreapp`cible un cadre `dotnet vstest` autre que , vous pouvez toujours exécuter la commande en passant dans le cadre ciblé avec un indicateur-cadre. Par exemple : `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 Mise à jour 5 et plus tard, le cadre souhaité est automatiquement détecté.

## <a name="see-also"></a>Voir aussi

- [Test unitaire avec test dotnet et xUnit](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec dotnet-test et NUnit](unit-testing-with-nunit.md)
- [Tests unitaires avec dotnet-test et MSTest](unit-testing-with-mstest.md)
