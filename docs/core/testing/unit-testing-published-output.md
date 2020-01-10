---
title: Tester la sortie publiée avec dotnet vstest
description: Découvrez comment exécuter des tests sur des bibliothèques publiées plutôt que sur le code source avec la commande dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714267"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="148a4-103">Tester la sortie publiée avec dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="148a4-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="148a4-104">Vous pouvez exécuter des tests sur la sortie déjà publiée à l’aide de la commande `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="148a4-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="148a4-105">Cela s’applique aux tests sur xUnit, MSTest et NUnit.</span><span class="sxs-lookup"><span data-stu-id="148a4-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="148a4-106">Recherchez simplement le fichier DLL qui faisait partie de votre sortie publiée et exécutez :</span><span class="sxs-lookup"><span data-stu-id="148a4-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="148a4-107">où `<MyPublishedTests>` est le nom de votre projet de test publié.</span><span class="sxs-lookup"><span data-stu-id="148a4-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="148a4-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="148a4-108">Example</span></span>

<span data-ttu-id="148a4-109">Les commandes ci-dessous montrent des tests en cours d’exécution sur une DLL publiée.</span><span class="sxs-lookup"><span data-stu-id="148a4-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="148a4-110">Remarque : Si votre application cible un Framework autre que `netcoreapp`, vous pouvez toujours exécuter la commande `dotnet vstest` en passant le Framework ciblé avec un indicateur Framework.</span><span class="sxs-lookup"><span data-stu-id="148a4-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="148a4-111">Par exemple, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="148a4-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="148a4-112">Dans Visual Studio 2017 Update 5 et les versions ultérieures, l’infrastructure souhaitée est détectée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="148a4-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="148a4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="148a4-113">See also</span></span>

- [<span data-ttu-id="148a4-114">Tests unitaires avec dotnet-test et xUnit</span><span class="sxs-lookup"><span data-stu-id="148a4-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="148a4-115">Tests unitaires avec dotnet-test et NUnit</span><span class="sxs-lookup"><span data-stu-id="148a4-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="148a4-116">Tests unitaires avec dotnet-test et MSTest</span><span class="sxs-lookup"><span data-stu-id="148a4-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
