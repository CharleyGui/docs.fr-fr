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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Guide pratique pour visualiser le contenu du Global Assembly Cache

Utilisez [l’outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Afficher les assemblys dans le GAC

Pour afficher une liste des assemblys dans leGlobal Assembly Cache, ouvrez [l’invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md), puis entrez la commande suivante :

```shell
gacutil -l
```

- ou -

```shell
gacutil /l
```

> [!NOTE]
> Dans les versions antérieures du .NET Framework, l’extension du shell Windows [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) vous permettait d’afficher le Global Assembly Cache dans l’Explorateur de fichiers. À partir de .NET Framework 4, Shfusion.dll est obsolète.

## <a name="see-also"></a>Voir aussi

- [Utilisation d'assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
