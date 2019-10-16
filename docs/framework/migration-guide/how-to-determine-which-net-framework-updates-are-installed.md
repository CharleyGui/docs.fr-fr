---
title: Guide pratique pour déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés
description: Découvrez comment déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c69d4bb370087dddafbfed41cbfb1fef229677c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318967"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Guide pratique pour déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés

Cet article montre comment rechercher les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur.

> [!NOTE]
> Toutes les techniques présentées dans cet article nécessitent un compte avec des privilèges administratifs.

## <a name="to-find-installed-updates-using-the-registry"></a>Pour rechercher les mises à jour installées à l’aide du Registre

Les correctifs logiciels et mises à jour de sécurité installés pour chaque version du .NET Framework installée sur un ordinateur sont répertoriés dans le Registre Windows. Vous pouvez utiliser le programme Éditeur du Registre (*regedit.exe*) pour afficher ces informations.

1. Ouvrez le programme **regedit.exe**. Dans Windows 8 et versions ultérieures, cliquez avec le bouton droit sur **Démarrer** ![la capture d’écran du logo de la touche Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), puis sélectionnez **exécuter**. Dans la zone **Ouvrir**, entrez **regedit** et sélectionnez **OK**.

2. Dans l'Éditeur du Registre, ouvrez la sous-clé suivante :

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Les mises à jour installées sont répertoriées sous les sous-clés qui identifient la version du .NET Framework auquel elles s'appliquent. Chaque mise à jour est identifiée par un numéro de Base de connaissances (KB).

Dans l'Éditeur du Registre, les versions du .NET Framework et les mises à jour installées pour chaque version sont stockées dans des sous-clés distinctes. Pour plus d’informations sur la détection des numéros des versions installées, consultez [Guide pratique pour déterminer les versions du .NET Framework installées](how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Pour rechercher les mises à jour installées en interrogeant le Registre dans le code

L’exemple suivant détermine par programmation les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur :

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Cet exemple produit une sortie semblable à la suivante :

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Pour rechercher les mises à jour installées en interrogeant le Registre dans PowerShell

L’exemple suivant montre comment déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur à l’aide de PowerShell :

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

Cet exemple produit une sortie semblable à la suivante :

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour déterminer les versions du .NET Framework installées](how-to-determine-which-versions-are-installed.md)
- [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md)
- [Versions et dépendances](versions-and-dependencies.md)
