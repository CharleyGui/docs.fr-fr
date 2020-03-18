---
title: -platform (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849870"
---
# <a name="-platform-c-compiler-options"></a>-platform (Options du compilateur C#)

Spécifie la version du CLR (Common Language Runtime) qui peut exécuter l’assembly.

## <a name="syntax"></a>Syntaxe

```console
-platform:string
```

## <a name="parameters"></a>Paramètres

`string` \
anycpu (valeur par défaut), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.

## <a name="remarks"></a>Notes 

- **anycpu** (valeur par défaut) compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme. Votre application s’exécute en tant que processus 64 bits dans la mesure du possible et repasse en 32 bits quand seul ce mode est disponible.

- **anycpu32bitpreferred** compile votre assembly pour qu’il s’exécute sur n’importe quelle plateforme. Votre application s’exécute en mode 32 bits sur les systèmes qui prennent en charge les applications 64 bits et 32 bits. Vous pouvez spécifier cette option uniquement pour les projets qui ciblent le .NET Framework 4.5.

- **ARM** compile votre assembly pour qu’il s’exécute sur un ordinateur doté d’un processeur ARM (Advanced RISC Machine).

- **ARM64** compile votre assembly pour s’exécuter par le CLR 64 bits sur un ordinateur qui dispose d’un processeur Advanced RISC Machine (ARM) qui prend en charge le jeu d’instructions A64.

- **x64** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d’instructions AMD64 ou EM64T.

- **x86** compile votre assembly pour qu’il soit exécuté par le CLR 32 bits x86.

- **Itanium** compile votre assembly pour qu’il soit exécuté par le CLR 64 bits sur un ordinateur doté d’un processeur Itanium.

Sur un système d'exploitation Windows 64 bits :

- Les assemblys compilés avec **-platform:x86** s’exécutent sur le CLR 32 bits fonctionnant sous WOW64.

- Une DLL compilée avec **-platform:anycpu** s’exécute sur le même CLR que le processus dans lequel elle est chargée.

- Les fichiers exécutables compilés avec **-platform:anycpu** s’exécutent sur le CLR 64 bits.

- Les fichiers exécutables compilés avec **-platform:anycpu32bitpreferred** s’exécutent sur le CLR 32 bits.

Le paramètre **anycpu32bitpreferred** ne vaut que pour les fichiers exécutables (.EXE) et nécessite le .NET Framework 4.5.

Pour plus d’informations sur le développement d’une application s’exécutant sur un système d’exploitation Windows 64 bits, consultez [Applications 64 bits](../../../framework/64-bit-apps.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la page **Propriétés** du projet.

2. Cliquez sur la page de propriétés **Générer**.

3. Modifiez la propriété **Plateforme cible** puis, pour les projets qui ciblent le .NET Framework 4.5, cochez ou décochez la case **Préférer 32 bits**.

> [!NOTE]
> `-platform`n’est pas disponible dans l’environnement de développement dans Visual C Express.

Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser l’option **-platform** pour préciser que l’application doit être exécutée par le CLR 64 bits sur un système d’exploitation Windows 64 bits.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
