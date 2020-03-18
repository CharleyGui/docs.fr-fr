---
title: Types référence - Référence C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744517"
---
# <a name="reference-types-c-reference"></a>Types référence (informations de référence sur C#)

Il existe deux genres de types en C# : les types référence et les types valeur. Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données. Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable. Avec les types valeur, chaque variable a sa propre copie des données et les opérations sur une variable ne peuvent pas affecter l’autre (sauf pour les variables de paramètre in, ref et out ; consultez les modificateurs de paramètre [in](in-parameter-modifier.md), [ref](ref.md) et [out](out-parameter-modifier.md)).

 Les mots clés suivants sont utilisés pour déclarer des types référence :

- [Classe](class.md)

- [Interface](interface.md)

- [Délégué](../builtin-types/reference-types.md)

 C# fournit également les types référence intégrés suivants :

- [Dynamique](../builtin-types/reference-types.md)

- [Objet](../builtin-types/reference-types.md)

- [String](../builtin-types/reference-types.md)

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Mots clés C#](index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types de valeur](../builtin-types/value-types.md)
