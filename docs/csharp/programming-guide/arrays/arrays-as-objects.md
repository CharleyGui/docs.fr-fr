---
title: Tableaux en tant qu'objets - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715089"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tableaux en tant qu'objets (guide de programmation C#)

En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++. <xref:System.Array> est le type de base abstrait de tous les types de tableau. Vous pouvez utiliser les propriétés et d’autres membres de classe que <xref:System.Array> possède. Par exemple, l’utilisation de la propriété <xref:System.Array.Length%2A> pour récupérer la longueur d’un tableau. Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.

## <a name="example"></a>Exemple

L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Tableaux](./index.md)
- [Tableaux unidimensionnels](./single-dimensional-arrays.md)
- [Tableaux multidimensionnels](./multidimensional-arrays.md)
- [Tableaux en escalier](./jagged-arrays.md)
