---
title: ReDim (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404276"
---
# <a name="redim-statement-visual-basic"></a>ReDim, instruction (Visual Basic)
Réalloue l'espace de stockage d'une variable tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|----------|----------------|  
|`Preserve`|Facultatif. Modificateur utilisé pour conserver les données du tableau existant quand vous modifiez la taille de la dernière dimension uniquement.|  
|`name`|Obligatoire. Nom de la variable de tableau. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Obligatoire. Liste des limites de chaque dimension du tableau redéfini.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser l'instruction `ReDim` pour modifier la taille d'une ou plusieurs dimensions d'un tableau qui a déjà été déclaré. Si vous possédez un grand tableau et que vous n'avez plus besoin de certains de ses éléments, `ReDim` peut libérer de la mémoire en réduisant la taille du tableau. En revanche, si votre tableau a besoin d'éléments supplémentaires, `ReDim` peut les ajouter.  
  
 L'instruction `ReDim` est destinée uniquement aux tableaux. Il n'est pas valide sur les scalaires (variables contenant une seule valeur), les collections ou les structures. Notez que si vous déclarez une variable de type `Array`, l'instruction `ReDim` ne dispose pas d'informations de type suffisantes pour créer le tableau.  
  
 Vous pouvez utiliser `ReDim` uniquement au niveau de la procédure. Par conséquent, le contexte de déclaration pour la variable doit être une procédure ; il ne peut pas être un fichier source, un espace de noms, une interface, une classe, une structure, un module ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Règles  
  
- **Variables multiples.** Vous pouvez redimensionner plusieurs variables de tableau dans la même instruction de déclaration et spécifier les `name` `boundlist` parties et pour chaque variable. Les variables multiples sont séparées par des virgules.  
  
- **Limites du tableau.** Chaque entrée dans `boundlist` peut spécifier les limites inférieure et supérieure de cette dimension. La limite inférieure est toujours 0 (zéro). La limite supérieure est la valeur d'index la plus élevée possible pour cette dimension, pas la longueur de la dimension (qui est la limite supérieure plus un). L'index pour chaque dimension varie de 0 à sa valeur liée supérieure.  
  
     Le nombre de dimensions dans `boundlist` doit correspondre au nombre de dimensions (rang) d'origine du tableau.  
  
- **Types de données.** L' `ReDim` instruction ne peut pas modifier le type de données d’une variable tableau ou de ses éléments.  
  
- **D’initialisation.** L' `ReDim` instruction ne peut pas fournir de nouvelles valeurs d’initialisation pour les éléments du tableau.  
  
- **Moteurs.** L' `ReDim` instruction ne peut pas modifier le rang (nombre de dimensions) du tableau.  
  
- **Redimensionnement avec Preserve.** Si vous utilisez `Preserve` , vous pouvez redimensionner uniquement la dernière dimension du tableau. Pour chaque autre dimension, vous devez spécifier la limite du tableau existant.  
  
     Par exemple, si votre tableau ne comporte qu'une seule dimension, vous pouvez la redimensionner tout en conservant le contenu du tableau, car vous modifiez la dernière et seule dimension. Toutefois, si votre tableau comporte deux dimensions ou plus, vous pouvez modifier la taille de la dernière dimension seulement si vous utilisez `Preserve`.  
  
- **Sous.** Vous pouvez utiliser `ReDim` sur une propriété qui contient un tableau de valeurs.  
  
## <a name="behavior"></a>Comportement  
  
- **Remplacement de tableau.** `ReDim`libère le tableau existant et crée un nouveau tableau avec le même rang. Le nouveau tableau remplace le tableau libéré dans la variable tableau.  
  
- **Initialisation sans Preserve.** Si vous ne spécifiez pas `Preserve` , `ReDim` Initialise les éléments du nouveau tableau en utilisant la valeur par défaut pour leur type de données.  
  
- **Initialisation avec Preserve.** Si vous spécifiez `Preserve` , Visual Basic copie les éléments du tableau existant dans le nouveau tableau.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant augmente la taille de la dernière dimension d'un tableau dynamique sans perte de données existantes dans le tableau, puis réduit la taille avec une perte de données partielle. Enfin, il réduit la taille à sa valeur d'origine et réinitialise tous les éléments du tableau.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 L'instruction `Dim` crée un tableau à trois dimensions. Étant donné que chaque dimension est déclarée avec une limite de 10, l'index de tableau pour chaque dimension peut aller de 0 à 10. Dans la discussion suivante, les trois dimensions sont appelées « couche », « ligne » et « colonne ».  
  
 La première instruction `ReDim` crée un tableau qui remplace le tableau existant dans la variable `intArray`. `ReDim` copie tous les éléments du tableau existant dans le nouveau tableau. Elle ajoute également 10 colonnes supplémentaires à la fin de chaque ligne dans chaque couche et initialise les éléments de ces nouvelles colonnes à 0 (la valeur par défaut d'`Integer`, qui est le type d'élément du tableau).  
  
 La deuxième instruction `ReDim` crée un autre tableau et copie tous les éléments adaptés. Toutefois, les cinq colonnes sont perdus à la fin de chaque ligne dans chaque couche. Cela n'est pas un problème si vous avez fini d'utiliser ces colonnes. La réduction de la taille d'un grand tableau peut libérer de la mémoire dont vous n'avez plus besoin.  
  
 La troisième instruction `ReDim` crée un autre tableau et supprime cinq autres colonnes de la fin de chaque ligne dans chaque couche. Cette fois-ci, elle ne copie pas les éléments existants. Cette instruction rétablit la taille d'origine du tableau. Étant donné que l'instruction n'inclut pas le modificateur `Preserve`, elle définit tous les éléments de tableau à leurs valeurs par défaut d'origine.  
  
 Pour obtenir des exemples supplémentaires, consultez [tableaux](../../programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IndexOutOfRangeException>
- [Const (instruction)](const-statement.md)
- [Dim (instruction)](dim-statement.md)
- [Erase (instruction)](erase-statement.md)
- [Résultat](../nothing.md)
- [Tableaux](../../programming-guide/language-features/arrays/index.md)
