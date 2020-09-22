---
title: GoTo, instruction
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
ms.openlocfilehash: 000f6754575bcce6b2d79d85541e755219aca956
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866618"
---
# <a name="goto-statement"></a>GoTo, instruction

Rebranche de manière inconditionnelle vers une ligne spécifiée dans une procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Élément  

 `line`  
 Obligatoire. Toute étiquette de ligne.  
  
## <a name="remarks"></a>Notes  

 L' `GoTo` instruction peut créer une branche uniquement vers les lignes de la procédure dans laquelle elle apparaît. La ligne doit avoir une étiquette de ligne qui `GoTo` peut faire référence à. Pour plus d’informations, consultez [Comment : étiqueter des instructions](../../programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo` les instructions peuvent rendre le code difficile à lire et à gérer. Dans la mesure du possible, utilisez une structure de contrôle à la place. Pour plus d’informations, consultez [Control Flow](../../programming-guide/language-features/control-flow/index.md).  
  
 Vous ne pouvez pas utiliser une `GoTo` instruction pour créer une branche à partir de l’extérieur d’un `For` ... `Next` , `For Each` ... `Next` ,. `SyncLock` .., `End SyncLock` `Try` . `Catch` .. ... `Finally` , `With` ... `End With` ou... `Using` `End Using` construction vers une étiquette à l’intérieur de.  
  
## <a name="branching-and-try-constructions"></a>Création de branche et d’essai  

 Au sein d’un `Try` ... `Catch` ...`Finally` , les règles suivantes s’appliquent à la création de branches avec l' `GoTo` instruction.  
  
|Bloc ou région|Créer une branche à partir de l’extérieur|Branchement hors de l’intérieur|  
|---------------------|-------------------------------|-------------------------------|  
|Bloc `Try`|Uniquement à partir d’un `Catch` bloc de la même construction <sup>1</sup>|Uniquement vers l’extérieur de la construction entière|  
|Bloc `Catch`|Jamais autorisé|Uniquement à l’extérieur de la construction entière ou au `Try` bloc de la même construction <sup>1</sup>|  
|Bloc `Finally`|Jamais autorisé|Jamais autorisé|  
  
 <sup>1</sup> s’il s’agit d’un `Try` ... `Catch` ...`Finally` la construction est imbriquée dans une autre, un `Catch` bloc peut créer une branche dans le `Try` bloc à son propre niveau d’imbrication, mais pas dans un autre `Try` bloc. Une instruction imbriquée `Try` ... `Catch` ...`Finally` la construction doit être entièrement contenue dans un `Try` `Catch` bloc ou de la construction dans laquelle elle est imbriquée.  
  
 L’illustration suivante montre une `Try` construction imbriquée dans une autre. Plusieurs branches parmi les blocs des deux constructions sont indiquées comme valides ou non valides.  
  
 ![Diagramme graphique de branchement dans des constructions Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `GoTo` instruction pour créer une branche vers les étiquettes de ligne dans une procédure.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi

- [Do...Loop (instruction)](do-loop-statement.md)
- [For...Next (instruction)](for-next-statement.md)
- [For Each...Next (instruction)](for-each-next-statement.md)
- [If...Then...Else (instruction)](if-then-else-statement.md)
- [Select...Case (instruction)](select-case-statement.md)
- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
- [While...End While (instruction)](while-end-while-statement.md)
- [With...End With (instruction)](with-end-with-statement.md)
