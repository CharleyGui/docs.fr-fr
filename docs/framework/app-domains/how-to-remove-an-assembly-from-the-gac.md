---
title: 'Procédure : supprimer un assembly du Global Assembly Cache'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa88cbc73415695a1545704a2ad8cab535f011e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053146"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Procédure : supprimer un assembly du Global Assembly Cache

Il existe deux façons de supprimer un assembly du Global Assembly Cache (GAC) :

- Utilisation de l’[outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md). Vous pouvez utiliser cette option pour désinstaller des assemblys que vous avez placés dans le GAC lors du développement et des tests.

- Utilisation de [Windows Installer](/windows/desktop/Msi/windows-installer-portal). Utilisez cette option pour désinstaller des assemblys quand vous testez des packages d'installation et pour les systèmes de production.

### <a name="removing-an-assembly-with-gacutilexe"></a>Suppression d'un assembly avec Gacutil.exe

1. À l'invite de commandes, tapez la commande suivante :

    **gacutil –u** \<*nom_assembly*>

    Dans cette commande, *nom_assembly* est le nom de l’assembly à supprimer du Global Assembly Cache.

    > [!WARNING]
    > Vous ne devez pas utiliser Gacutil.exe pour supprimer des assemblys sur des systèmes de production, en raison de la possibilité que l'assembly soit encore requis par certaines applications. Au lieu de cela, vous devez utiliser Windows Installer, qui conserve un comptage des références pour chaque assembly qu'il installe dans le GAC.

 L'exemple suivant supprime un assembly nommé `hello.dll` du Global Assembly Cache.

```
gacutil -u hello
```

### <a name="removing-an-assembly-with-windows-installer"></a>Suppression d'un assembly avec Windows Installer

1. Dans l’application **Programmes et fonctionnalités** du **Panneau de configuration**, sélectionnez l’application que vous voulez désinstaller. Si le package d'installation a placé les assemblys dans le GAC, Windows Installer les supprime s'ils ne sont pas utilisés par une autre application.

    > [!NOTE]
    > Windows Installer conserve un comptage des références pour les assemblys installés dans le GAC. Un assembly est supprimé du GAC seulement quand son comptage des références atteint zéro, ce qui indique qu'il n'est utilisé par aucune application installée par un package Windows Installer.

## <a name="see-also"></a>Voir aussi

- [Utilisation d’assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Guide pratique pour installer un assembly dans le Global Assembly Cache](install-assembly-into-gac.md)
- [Gacutil.exe (outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
