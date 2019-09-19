---
title: Tester la sortie publiée avec dotnet vstest
description: Découvrez comment exécuter des tests sur des bibliothèques publiées plutôt que sur le code source avec la commande dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117030"
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
> Remarque : si votre application cible une version de .NET Framework autre que `netcoreapp`, vous pouvez toujours exécuter la commande `dotnet vstest` en passant à la version de .NET Framework ciblée avec un indicateur de .NET Framework. Par exemple, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Dans Visual Studio 2017 Update 5, la version souhaitée du .NET framework est automatiquement détectée.

## <a name="see-also"></a>Voir aussi

- [Tests unitaires avec dotnet-test et xUnit](unit-testing-with-dotnet-test.md)
- [Tests unitaires avec dotnet-test et NUnit](unit-testing-with-nunit.md)
- [Tests unitaires avec dotnet-test et MSTest](unit-testing-with-mstest.md)
