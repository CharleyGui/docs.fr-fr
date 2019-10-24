---
title: Tester la sortie publiée avec dotnet vstest
description: Découvrez comment exécuter des tests sur des bibliothèques publiées plutôt que sur le code source avec la commande dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: e4fd25dc9ff30bdfe85cd1167a1dc41ea20a5f80
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771927"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Tester la sortie publiée avec dotnet vstest

Vous pouvez exécuter des tests sur la sortie déjà publiée à l’aide de la commande `dotnet vstest`. Cela s’applique aux tests sur xUnit, MSTest et NUnit. Recherchez simplement le fichier DLL qui faisait partie de votre sortie publiée et exécutez :

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

où `<MyPublishedTests>` est le nom de votre projet de test publié.

## <a name="example"></a>Exemple

Les commandes ci-dessous montrent des tests en cours d’exécution sur une DLL publiée.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Remarque : Si votre application cible un Framework autre que `netcoreapp`, vous pouvez toujours exécuter la commande `dotnet vstest` en passant le Framework ciblé avec un indicateur Framework. Par exemple, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 Update 5 et les versions ultérieures, l’infrastructure souhaitée est détectée automatiquement.

## <a name="see-also"></a>Voir aussi

- [Tests unitaires avec dotnet-test et xUnit](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec dotnet-test et NUnit](unit-testing-with-nunit.md)
- [Tests unitaires avec dotnet-test et MSTest](unit-testing-with-mstest.md)
