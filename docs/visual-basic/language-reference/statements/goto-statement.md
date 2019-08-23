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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912447"
---
# <a name="goto-statement"></a>GoTo, instruction
Rebranche de manière inconditionnelle vers une ligne spécifiée dans une procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Élément  
 `line`  
 Requis. Toute étiquette de ligne.  
  
## <a name="remarks"></a>Notes  
 L' `GoTo` instruction peut créer une branche uniquement vers les lignes de la procédure dans laquelle elle apparaît. La ligne doit avoir une étiquette de ligne `GoTo` qui peut faire référence à. Pour plus d’informations, consultez [Guide pratique pour ](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)Étiquettes.  
  
> [!NOTE]
> `GoTo`les instructions peuvent rendre le code difficile à lire et à gérer. Dans la mesure du possible, utilisez une structure de contrôle à la place. Pour plus d’informations, consultez [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Vous ne pouvez pas `GoTo` utiliser une instruction pour créer une `For`branche à partir de l’extérieur d’un... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, ou`Using`... `End Using` construction d’une étiquette à l’intérieur de.  
  
## <a name="branching-and-try-constructions"></a>Création de branche et d’essai  
 Au sein `Try`d’un... `Catch`... , les règles suivantes s’appliquent à la création de `GoTo` branches avec l’instruction. `Finally`  
  
|Bloc ou région|Créer une branche à partir de l’extérieur|Branchement hors de l’intérieur|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`plage|Uniquement à partir `Catch` d’un bloc de la même construction <sup>1</sup>|Uniquement vers l’extérieur de la construction entière|  
|`Catch`plage|Jamais autorisé|Uniquement à l’extérieur de la construction entière ou au `Try` bloc de la même construction <sup>1</sup>|  
|`Finally`plage|Jamais autorisé|Jamais autorisé|  
  
 <sup>1</sup> s’il `Try`s’agit d’un... `Catch`... la construction est imbriquée dans une autre `Catch` , un bloc peut créer `Try` une branche dans le bloc à son propre niveau d’imbrication, mais `Try` pas dans un autre bloc. `Finally` Une instruction imbriquée `Try`... `Catch`... la construction doit être entièrement contenue `Try` dans `Catch` un bloc ou de la construction dans laquelle elle est imbriquée. `Finally`  
  
 L’illustration suivante montre une `Try` construction imbriquée dans une autre. Plusieurs branches parmi les blocs des deux constructions sont indiquées comme valides ou non valides.  
  
 ![Diagramme graphique de branchement dans des constructions Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Exemples  
 L’exemple suivant utilise l' `GoTo` instruction pour créer une branche vers les étiquettes de ligne dans une procédure.  
  
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
