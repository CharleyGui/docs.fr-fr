---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348653"
---
# <a name="-refout-visual-basic"></a>-REFOUT (Visual Basic)

L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

`filepath`  
Chemin d’accès et nom de fichier de l’assembly de référence. Il doit généralement se trouver dans un sous-dossier de l’assembly principal. La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal. Tous les dossiers `filepath` dans doivent exister. le compilateur ne les crée pas.

## <a name="remarks"></a>Notes

Visual Basic prend en `-refout` charge le commutateur à partir de la version 15,3.

Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque. Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API. Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.

Les `-refout` options [`-refonly`](refonly-compiler-option.md) et s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [-refonly](refonly-compiler-option.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
