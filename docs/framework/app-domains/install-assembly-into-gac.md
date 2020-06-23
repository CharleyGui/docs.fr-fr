---
title: 'Procédure : installer un assembly dans le Global Assembly Cache'
description: Installez un assembly dans le Global Assembly Cache (GAC) dans .NET afin qu’il puisse être partagé par de nombreuses applications. Utilisez Windows Installer ou l’utilitaire GAC.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104663"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Procédure : installer un assembly dans le Global Assembly Cache

Le Global Assembly Cache (GAC) stocke des assemblys partagés par plusieurs applications. Installez un assembly dans le [Global Assembly Cache](gac.md) avec l’un des composants suivants :

- [Windows Installer](#windows-installer)
- [Outil global assembly cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> Vous pouvez installer uniquement des assemblys avec nom fort dans le Global Assembly Cache. Pour plus d’informations sur la création d’un assembly avec nom fort, consultez [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), le moteur d’installation de Windows, est la méthode recommandée pour ajouter des assemblys dans le Global Assembly Cache. Windows Installer fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages. Pour créer un package de programme d’installation pour Windows Installer, utilisez l’[extension de l’ensemble d’outils WiX pour Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Global Assembly Cache (outil)

Vous pouvez utiliser l' [utilitaire .net global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter des assemblys au global assembly cache et afficher le contenu de l’global assembly cache.

   > [!NOTE]
   > L’outil *gacutil.exe* est réservé au développement. Ne vous en servez pas pour installer des assemblys de production dans le Global Assembly Cache.

Pour installer un assembly dans le GAC à l’aide de *gacutil.exe*, utilisez cette syntaxe :

```cmd
gacutil -i <assembly name>
```

Dans cette commande, *\<assembly name>* est le nom de l’assembly à installer dans le global assembly cache.

Si *gacutil.exe* ne se trouve pas dans votre chemin d’accès système, utilisez l' [invite de commandes développeur pour Visual Studio *\<version>* ](../tools/developer-command-prompt-for-vs.md).

L’exemple suivant installe un assembly sous le nom de fichier *hello.dll* dans le Global Assembly Cache.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> Dans les versions précédentes du .NET Framework, l’extension d’environnement Windows *Shfusion.dll* permet de faire glisser des assemblys dans l’Explorateur de fichiers pour les installer. Depuis .NET Framework 4, *Shfusion.dll* est obsolète.

## <a name="see-also"></a>Voir aussi

- [Utiliser des assemblys et le Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Comment : supprimer un assembly du Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (outil global assembly cache)](../tools/gacutil-exe-gac-tool.md)
- [Comment : signer un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md)
