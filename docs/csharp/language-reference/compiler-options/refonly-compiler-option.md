---
title: -refonly (Options du compilateur C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606488"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (Options du compilateur C#)

L’option **-refonly** indique qu’un assembly de référence doit être généré à la place d’un assembly d’implémentation, en tant que sortie principale. Le paramètre `-refonly` désactive sans assistance la génération de fichiers PDB, car les assemblys de référence ne peuvent pas être exécutés. Cette option correspond à la propriété de projet [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) de MSBuild.

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Remarques

Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes. L’utilisation de corps `throw null` (plutôt qu’aucun corps) permet la bonne exécution de PEVerify (et, par voie de conséquence, la validation de la conformité des métadonnées).

Les assemblys de référence incluent un attribut `ReferenceAssembly` de niveau assembly. Cet attribut peut être spécifié dans la source (le compilateur n’a plus alors besoin de le synthétiser). En raison de cet attribut, les runtimes refusent de charger les assemblys de référence pour l’exécution (mais ils peuvent toujours être chargés en mode de réflexion uniquement). Les outils reflétés dans les assemblys doivent absolument charger les assemblys de référence en mode réflexion uniquement, sinon ils reçoivent une erreur de chargement de type de la part du runtime.

En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :

- Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API. L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques. Par exemple, l’assembly de référence pour `class C { private void M() { dynamic d = 1; ... } }` ne référence aucun des types requis pour `dynamic`.
- Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement. S’il n’y a aucun attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, faites de même pour les membres de fonction internes.
- Toutefois, tous les types (y compris les types privés ou imbriqués) sont conservés dans les assemblys de référence. Tous les attributs sont conservés (même les attributs internes).
- Toutes les méthodes virtuelles sont conservées. Les implémentations d’interface explicite sont conservées. Les propriétés et les événements implémentés explicitement sont conservés, car leurs accesseurs sont virtuels (et donc conservés).
- Tous les champs d’un struct sont conservés. (Candidat pour une optimisation future de C# 7.1)

Les options `-refonly` et [`-refout`](refout-compiler-option.md) s’excluent mutuellement.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
