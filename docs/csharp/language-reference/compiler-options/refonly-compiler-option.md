---
title: -refonly (Options du compilateur C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773852"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (Options du compilateur C#)

L’option **-refonly** indique qu’un assembly de référence doit être généré à la place d’un assembly d’implémentation, en tant que sortie principale. Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés. Cette option correspond à la propriété de projet [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Notes 

Les assemblages de référence sont un type spécial d’assemblage qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface publique de l’API de la bibliothèque. Elles comprennent des déclarations pour tous les membres qui sont importantes lorsqu’ils font référence à une assemblée dans des outils de construction, mais excluent toutes les mises en œuvre et déclarations des membres du groupe privé qui n’ont aucune incidence observable sur leur contrat d’API. Pour plus d’informations, voir [les assemblages de référence](../../../standard/assembly/reference-assemblies.md) dans .NET Guide.

Les `-refonly` [`-refout`](refout-compiler-option.md) options et les options s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
