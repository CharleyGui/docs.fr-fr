---
title: Tableaux en tant qu'objets - Guide de programmation C#
description: Les tableaux en C# sont des objets du tableau de types de base abstraits. Vous pouvez utiliser les propriétés et d’autres membres de classe de Array, tels que la propriété Length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474720"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tableaux en tant qu'objets (guide de programmation C#)

En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++. <xref:System.Array> est le type de base abstrait de tous les types de tableau. Vous pouvez utiliser les propriétés et d’autres membres de classe qui <xref:System.Array> possèdent. Par exemple, l’utilisation de la <xref:System.Array.Length%2A> propriété pour récupérer la longueur d’un tableau. Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.

## <a name="example"></a>Exemple

L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Tableaux](./index.md)
- [Tableaux unidimensionnels](./single-dimensional-arrays.md)
- [Tableaux multidimensionnels](./multidimensional-arrays.md)
- [Tableaux en escalier](./jagged-arrays.md)
