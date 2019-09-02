---
title: Tester la sortie publiée avec dotnet vstest
description: Découvrez comment exécuter des tests sur des bibliothèques publiées plutôt que sur le code source avec la commande dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9ac03053bc762d0176e087545871ca8a145cd41e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168295"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Tester la sortie publiée avec dotnet vstest

Vous pouvez exécuter des tests sur la sortie déjà publiée à l’aide de la commande `dotnet vstest`. Cela s’applique aux tests sur xUnit, MSTest et NUnit. Recherchez simplement le fichier DLL qui faisait partie de votre sortie publiée et exécutez :

```console
dotnet vstest <MyPublishedTests>.dll
```

où `<MyPublishedTests>` est le nom de votre projet de test publié.

## <a name="example"></a>Exemples

Les commandes ci-dessous montrent des tests en cours d’exécution sur une DLL publiée.

```console
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Remarque : si votre application cible une version de .NET Framework autre que `netcoreapp`, vous pouvez toujours exécuter la commande `dotnet vstest` en passant à la version de .NET Framework ciblée avec un indicateur de .NET Framework. Par exemple, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 Update 5, la version souhaitée du .NET framework est automatiquement détectée.

## <a name="see-also"></a>Voir aussi

- [Tests unitaires avec dotnet-test et xUnit](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec dotnet-test et NUnit](unit-testing-with-nunit.md)
- [Tests unitaires avec dotnet-test et MSTest](unit-testing-with-mstest.md)
