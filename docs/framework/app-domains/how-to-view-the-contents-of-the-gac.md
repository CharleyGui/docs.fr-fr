---
title: 'Procédure : Visualiser le contenu du Global Assembly Cache'
description: Découvrez comment afficher le contenu de la Global Assembly Cache dans .NET à l’aide de l’outil Global Assembly Cache (GAC) (gacutil.exe).
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: 8b81f78f4ea28b3b9fca374029fe49f809826d8e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558561"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="7f177-103">Guide pratique pour visualiser le contenu du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="7f177-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="7f177-104">Utilisez [l’outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="7f177-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="7f177-105">Afficher les assemblys dans le GAC</span><span class="sxs-lookup"><span data-stu-id="7f177-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="7f177-106">Pour afficher une liste des assemblys dans leGlobal Assembly Cache, ouvrez [l’invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md), puis entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7f177-106">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="7f177-107">- ou -</span><span class="sxs-lookup"><span data-stu-id="7f177-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="7f177-108">Dans les versions antérieures du .NET Framework, l’extension du shell Windows [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) vous permettait d’afficher le Global Assembly Cache dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7f177-108">In earlier versions of the .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="7f177-109">À partir de .NET Framework 4, Shfusion.dll est obsolète.</span><span class="sxs-lookup"><span data-stu-id="7f177-109">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f177-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f177-110">See also</span></span>

- [<span data-ttu-id="7f177-111">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="7f177-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="7f177-112">Gacutil.exe (Outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="7f177-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
