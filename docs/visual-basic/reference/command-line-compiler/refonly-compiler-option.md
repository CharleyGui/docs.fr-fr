---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775567"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

L’option **-refonly** indique que la sortie principale de la compilation doit être un assembly de référence au lieu d’un assembly d’implémentation. Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Notes

Visual Basic prend en charge le commutateur `-refonly` à partir de la version 15,3.

Les assemblys de référence sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque. Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API. Pour plus d’informations, consultez [références des assemblys](../../../standard/assembly/reference-assemblies.md) dans le guide .net.

Les options `-refonly` et [`-refout`](refout-compiler-option.md) s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [/refout](refout-compiler-option.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
