---
title: GoTo, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581817"
---
# <a name="goto-statement"></a>GoTo, instruction
Rebranche de manière inconditionnelle vers une ligne spécifiée dans une procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Élément  
 `line`  
 Requis. Toute étiquette de ligne.  
  
## <a name="remarks"></a>Notes  
 L’instruction `GoTo` peut créer une branche uniquement vers les lignes de la procédure dans laquelle elle apparaît. La ligne doit avoir une étiquette de ligne à laquelle `GoTo` peut faire référence. Pour plus d’informations, consultez [Comment : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> les instructions `GoTo` peuvent rendre le code difficile à lire et à gérer. Dans la mesure du possible, utilisez une structure de contrôle à la place. Pour plus d’informations, consultez [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Vous ne pouvez pas utiliser une instruction `GoTo` pour créer une branche à partir de l’extérieur d’un `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, 0... 1 ou 2... 3 construction à une étiquette à l’intérieur de.  
  
## <a name="branching-and-try-constructions"></a>Création de branche et d’essai  
 Au sein d’un `Try`... `Catch`... `Finally` construction, les règles suivantes s’appliquent à la création de branche avec l’instruction `GoTo`.  
  
|Bloc ou région|Créer une branche à partir de l’extérieur|Branchement hors de l’intérieur|  
|---------------------|-------------------------------|-------------------------------|  
|bloc `Try`|Uniquement à partir d’un bloc `Catch` de la même construction <sup>1</sup>|Uniquement vers l’extérieur de la construction entière|  
|bloc `Catch`|Jamais autorisé|Uniquement à l’extérieur de la construction entière ou au bloc `Try` de la même construction <sup>1</sup>|  
|bloc `Finally`|Jamais autorisé|Jamais autorisé|  
  
 <sup>1</sup> si une `Try`... `Catch`... `Finally` construction est imbriquée dans une autre, un bloc `Catch` peut créer une branche dans le bloc `Try` à son propre niveau d’imbrication, mais pas dans un autre bloc `Try`. Une `Try` imbriquée... `Catch`... `Finally` construction doit être entièrement contenue dans un bloc `Try` ou `Catch` de la construction dans laquelle elle est imbriquée.  
  
 L’illustration suivante montre une construction `Try` imbriquée dans une autre. Plusieurs branches parmi les blocs des deux constructions sont indiquées comme valides ou non valides.  
  
 ![Diagramme graphique de branchement dans des constructions Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `GoTo` pour créer une branche vers les étiquettes de ligne dans une procédure.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next (instruction)](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case (instruction)](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With (instruction)](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
