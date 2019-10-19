---
title: -REFOUT (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582869"
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
Chemin d’accès et nom de fichier de l’assembly de référence. Il doit généralement se trouver dans un sous-dossier de l’assembly principal. La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal. Tous les dossiers de `filepath` doivent exister. le compilateur ne les crée pas.

## <a name="remarks"></a>Notes

Visual Basic prend en charge le commutateur `-refout` à partir de la version 15,3.

Les assemblys de référence sont des assemblys de métadonnées uniquement qui contiennent des métadonnées, mais pas de code d’implémentation. Ils incluent des informations sur les types et les membres pour tout sauf les types anonymes. Leurs corps de méthode sont remplacés par une seule instruction `throw null`. La raison de l’utilisation de `throw null` corps de méthode (par opposition à aucun corps) est que PEVerify peut s’exécuter et réussir (validant ainsi l’exhaustivité des métadonnées).

Les assemblys de référence incluent un attribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) au niveau de l’assembly. Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser). En raison de cet attribut, les runtimes refusent de charger des assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés dans un contexte de réflexion uniquement). Les outils qui reflètent sur les assemblys doivent s’assurer qu’ils chargent des assemblys de référence en tant que réflexion uniquement ; dans le cas contraire, le runtime lève une <xref:System.BadImageFormatException>.

Les options `-refout` et [`-refonly`](refonly-compiler-option.md) s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [-refonly](refonly-compiler-option.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
