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
ms.openlocfilehash: 4d775efc073f3aad745eff7a7707efdec06172c2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104687"
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

- [Utilisation d'assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
