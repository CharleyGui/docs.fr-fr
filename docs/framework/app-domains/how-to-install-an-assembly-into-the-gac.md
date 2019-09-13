---
title: 'Procédure : installer un assembly dans le Global Assembly Cache'
ms.date: 02/05/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926514"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Procédure : installer un assembly dans le Global Assembly Cache

Le Global Assembly Cache (GAC) stocke des assemblys partagés par plusieurs applications. Installez un assembly dans le [Global Assembly Cache](gac.md) avec l’un des composants suivants : 

- [Windows Installer](#windows-installer)
- [Outil Global Assembly Cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> Vous ne pouvez installer dans le GAC que des assemblys à nom fort. Pour savoir comment créer un assembly à nom fort, consultez [Guide pratique pour signer un assembly avec un nom fort](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), le moteur d’installation de Windows, est la méthode recommandée pour ajouter des assemblys dans le Global Assembly Cache. Windows Installer fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages. Pour créer un package de programme d’installation pour Windows Installer, utilisez l’[extension de l’ensemble d’outils WiX pour Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Outil Global Assembly Cache

Vous pouvez utiliser l’[outil Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter des assemblys au Global Assembly Cache et visualiser le contenu de ce cache.

   > [!NOTE]
   > L’outil *gacutil.exe* est réservé au développement. Ne vous en servez pas pour installer des assemblys de production dans le Global Assembly Cache.

Pour installer un assembly dans le GAC à l’aide de *gacutil.exe*, utilisez cette syntaxe :

```console
gacutil -i <assembly name>
```

Dans cette commande, *\<assembly name>* est le nom de l’assembly à installer dans le Global Assembly Cache.

Si *gacutil.exe* ne se trouve pas dans le chemin de votre système, utilisez l’[invite de commandes développeur pour VS *\<version>* ](../tools/developer-command-prompt-for-vs.md).

L’exemple suivant installe un assembly sous le nom de fichier *hello.dll* dans le Global Assembly Cache.

```console
gacutil -i hello.dll
```

> [!NOTE]
> Dans les versions précédentes du .NET Framework, l’extension d’environnement Windows *Shfusion.dll* permet de faire glisser des assemblys dans l’Explorateur de fichiers pour les installer. Depuis .NET Framework 4, *Shfusion.dll* est obsolète.

## <a name="see-also"></a>Voir aussi

- [Utilisation d’assemblys et du Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Guide pratique : supprimer un assembly du Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
- [Guide pratique : signer un assembly avec un nom fort](how-to-sign-an-assembly-with-a-strong-name.md)
