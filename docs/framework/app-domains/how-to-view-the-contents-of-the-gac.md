---
title: Guide pratique pour visualiser le contenu du Global Assembly Cache
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
ms.openlocfilehash: b5d8b31e7eb23789878da620f3a4517056a1ee3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119830"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Guide pratique pour visualiser le contenu du Global Assembly Cache

Utilisez [l’outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Afficher les assemblys dans le GAC

Pour afficher une liste des assemblys dans leGlobal Assembly Cache, ouvrez [l’invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md), puis entrez la commande suivante :

```shell
gacutil -l
```

-ou-

```shell
gacutil /l
```

> [!NOTE]
> Dans les versions antérieures du .NET Framework, l’extension du shell Windows [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) vous permettait d’afficher le Global Assembly Cache dans l’Explorateur de fichiers. À partir de .NET Framework 4, Shfusion.dll est obsolète.

## <a name="see-also"></a>Voir aussi

- [Utilisation d’assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Gacutil. exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
