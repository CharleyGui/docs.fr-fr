---
title: Guide pratique pour installer un assembly dans le Global Assembly Cache
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155561"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Guide pratique pour installer un assembly dans le Global Assembly Cache

Le Global Assembly Cache (GAC) stocke des assemblys partagés par plusieurs applications. Installez un assembly dans le [Global Assembly Cache](gac.md) avec l’un des composants suivants :

- [Installateur Windows](#windows-installer)
- [Outil Global Assembly Cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> Vous ne pouvez installer que des assemblages nommés fort dans le cache d’assemblage global. Pour plus d’informations sur la façon de créer un assemblage fort, voir [Comment: Signez une assemblée avec un nom fort](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), le moteur d’installation de Windows, est la méthode recommandée pour ajouter des assemblys dans le Global Assembly Cache. Windows Installer fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages. Pour créer un package de programme d’installation pour Windows Installer, utilisez l’[extension de l’ensemble d’outils WiX pour Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Global Assembly Cache (outil)

Vous pouvez utiliser [l’utilitaire .NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter des assemblages au cache d’assemblage global et pour afficher le contenu du cache d’assemblage global.

   > [!NOTE]
   > L’outil *gacutil.exe* est réservé au développement. Ne vous en servez pas pour installer des assemblys de production dans le Global Assembly Cache.

Pour installer un assembly dans le GAC à l’aide de *gacutil.exe*, utilisez cette syntaxe :

```cmd
gacutil -i <assembly name>
```

Dans cette commande, * \<le nom d’assemblage>* est le nom de l’assemblage à installer dans le cache d’assemblage global.

Si *gacutil.exe* n’est pas dans votre trajectoire de système, utilisez [l’invite de commande de développeur pour * \<la version *VS>](../tools/developer-command-prompt-for-vs.md).

L’exemple suivant installe un assembly sous le nom de fichier *hello.dll* dans le Global Assembly Cache.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> Dans les versions précédentes du .NET Framework, l’extension d’environnement Windows *Shfusion.dll* permet de faire glisser des assemblys dans l’Explorateur de fichiers pour les installer. Depuis .NET Framework 4, *Shfusion.dll* est obsolète.

## <a name="see-also"></a>Voir aussi

- [Travailler avec les assemblées et le cache d’assemblage global](working-with-assemblies-and-the-gac.md)
- [Comment : Supprimer une assemblée du cache d’assemblage global](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
- [Comment: Signer une assemblée avec un nom fort](../../standard/assembly/sign-strong-name.md)
