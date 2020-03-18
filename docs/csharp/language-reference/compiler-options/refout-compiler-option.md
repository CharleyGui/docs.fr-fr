---
title: -refout (Options du compilateur C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771756"
---
# <a name="-refout-c-compiler-options"></a>-refout (Options du compilateur C#)

L’option **-refout** spécifie un chemin de fichier où l’assembly de référence doit être généré. Cela se traduit par `metadataPeStream` dans l’API Emit. Cette option correspond à la propriété de projet [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Chemin de l’assembly de référence. Il doit généralement correspondre à celui de l’assembly principal. La convention recommandée (utilisée par MSBuild) consiste à placer l’assembly de référence dans un sous-dossier « ref/ » par rapport à l’assembly principal.

## <a name="remarks"></a>Notes 

Les assemblages de référence sont un type spécial d’assemblage qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface publique de l’API de la bibliothèque. Elles comprennent des déclarations pour tous les membres qui sont importantes lorsqu’ils font référence à une assemblée dans des outils de construction, mais excluent toutes les mises en œuvre et déclarations des membres du groupe privé qui n’ont aucune incidence observable sur leur contrat d’API. Pour plus d’informations, voir [les assemblages de référence](../../../standard/assembly/reference-assemblies.md) dans .NET Guide.

Les `-refout` [`-refonly`](refonly-compiler-option.md) options et les options s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
