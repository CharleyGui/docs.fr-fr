---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e8607f8254783b5486b02ccc4c7e4081da506fae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802149"
---
# <a name="-subsystemversion-visual-basic"></a>-SubSystemVersion (Visual Basic)

Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, déterminant ainsi les versions de Windows sur lesquelles le fichier exécutable peut s’exécuter. En règle générale, cette option garantit que le fichier exécutable peut tirer parti de fonctionnalités de sécurité particulières qui ne sont pas disponibles avec des versions antérieures de Windows.

> [!NOTE]
> Pour spécifier le sous-système lui-même, utilisez l’option du compilateur [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).

## <a name="syntax"></a>Syntaxe

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Paramètres

`major.minor`

Version minimale requise du sous-système, telle qu’elle est exprimée dans une notation par points pour les versions majeure et mineure. Par exemple, vous pouvez spécifier qu’une application ne peut pas s’exécuter sur un système d’exploitation antérieur à Windows 7 si vous définissez la valeur de cette option sur 6.01, comme décrit dans le tableau plus loin dans cette rubrique. Vous devez spécifier les valeurs de `major` et `minor` en tant qu’entiers.

Les zéros à gauche du numéro de version `minor` ne modifient pas la version, contrairement aux zéros de droite. Par exemple, 6.1 et 6.01 font référence à la même version, mais 6.10 fait référence à une version différente. Nous vous recommandons d’exprimer la version mineure avec deux chiffres pour éviter toute confusion.

## <a name="remarks"></a>Notes

Le tableau suivant répertorie les versions courantes de sous-système de Windows.

|Version de Windows|Version de sous-système|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5,01|
|Windows Server 2003|5.02|
|Windows Vista|6,00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Valeurs par défaut

La valeur par défaut de l’option du compilateur **-subsystemversion** dépend des conditions répertoriées dans la liste suivante :

- La valeur par défaut est 6.02 si l’une quelconque des options du compilateur de la liste suivante est définie :

  - [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)

- La valeur par défaut est 6.00 si vous utilisez MSBuild, si vous ciblez .NET Framework 4.5 et si vous n’avez défini aucune des options du compilateur spécifiées plus haut dans cette liste.

- La valeur par défaut est 4.00 si aucune des conditions précédentes n’est vraie.

## <a name="setting-this-option"></a>Définition de cette option

Pour définir l’option de compilateur **-SubSystemVersion** dans Visual Studio, vous devez ouvrir le fichier. vbproj et spécifier une valeur pour `SubsystemVersion` la propriété dans le code XML MSBuild. Vous ne pouvez pas définir cette option dans l’environnement IDE de Visual Studio. Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [Propriétés communes des projets MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)

- [Propriétés MSBuild](/visualstudio/msbuild/msbuild-properties)
