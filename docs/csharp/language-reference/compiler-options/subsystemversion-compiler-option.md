---
title: -subsystemversion (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802032"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (Options du compilateur C#)

Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, déterminant ainsi les versions de Windows sur lesquelles le fichier exécutable peut s’exécuter. En règle générale, cette option garantit que le fichier exécutable peut tirer parti de fonctionnalités de sécurité particulières qui ne sont pas disponibles avec des versions antérieures de Windows.

> [!NOTE]
> Pour spécifier le sous-système lui-même, utilisez l’option du compilateur [-target](./target-compiler-option.md).

## <a name="syntax"></a>Syntaxe

```console
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
|Windows 2000|5.00|
|Windows XP|5,01|
|Windows Server 2003|5.02|
|Windows Vista|6,00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Valeurs par défaut

La valeur par défaut de l’option du compilateur **-subsystemversion** dépend des conditions répertoriées dans la liste suivante :

- La valeur par défaut est 6.02 si l’une quelconque des options du compilateur de la liste suivante est définie :

  - [-cible:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [/target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platform:arm](./platform-compiler-option.md)

- La valeur par défaut est 6.00 si vous utilisez MSBuild, si vous ciblez .NET Framework 4.5 et si vous n’avez défini aucune des options du compilateur spécifiées plus haut dans cette liste.

- La valeur par défaut est 4.00 si aucune des conditions précédentes n’est vraie.

## <a name="setting-this-option"></a>Définition de cette option

Pour définir l’option du compilateur **-subsystemversion** dans Visual Studio, vous devez ouvrir le fichier .csproj et spécifier une valeur pour la propriété `SubsystemVersion` dans le code XML MSBuild. Vous ne pouvez pas définir cette option dans l’environnement IDE de Visual Studio. Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [Propriétés communes des projets MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
