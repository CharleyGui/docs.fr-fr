---
title: Continue (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382092"
---
# <a name="continue-statement-visual-basic"></a>Continue, instruction (Visual Basic)
Transfère immédiatement le contrôle à l’itération suivante d’une boucle.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez transférer de l’intérieur d’une `Do` `For` boucle, ou `While` vers l’itération suivante de cette boucle. Le contrôle est immédiatement passé au test de condition de boucle, ce qui équivaut à effectuer un transfert vers l' `For` `While` instruction ou, ou à l' `Do` `Loop` instruction ou qui contient la `Until` `While` clause ou.  
  
 Vous pouvez utiliser `Continue` à n’importe quel emplacement de la boucle qui autorise les transferts. Les règles autorisant le transfert de contrôle sont les mêmes que celles de l' [instruction goto](goto-statement.md).  
  
 Par exemple, si une boucle est entièrement contenue dans un bloc `Try` , un `Catch` bloc ou un `Finally` bloc, vous pouvez utiliser `Continue` pour transférer en dehors de la boucle. Si, en revanche, la `Try` structure... `End Try` est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle hors du `Finally` bloc, et vous pouvez l’utiliser pour le transfert en dehors d’un `Try` `Catch` bloc ou uniquement si vous transférez complètement en dehors de la `Try` structure... `End Try` .  
  
 Si vous disposez de boucles imbriquées du même type, par exemple une `Do` boucle dans une autre `Do` boucle, une `Continue Do` instruction passe à l’itération suivante de la boucle la plus profonde `Do` qui la contient. Vous ne pouvez pas utiliser `Continue` pour passer à l’itération suivante d’une boucle conteneur du même type.  
  
 Si vous avez des boucles imbriquées de types différents, par exemple une `Do` boucle dans une `For` boucle, vous pouvez passer à l’itération suivante de l’une ou l’autre boucle à l’aide de `Continue Do` ou de `Continue For` .  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise l' `Continue While` instruction pour passer à la colonne suivante d’un tableau si un diviseur est égal à zéro. `Continue While`Est à l’intérieur d’une `For` boucle. Elle est transférée à l' `While col < lastcol` instruction, qui est l’itération suivante de la boucle la plus profonde `While` qui contient la `For` boucle.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Do...Loop (instruction)](do-loop-statement.md)
- [For...Next (instruction)](for-next-statement.md)
- [While...End While (instruction)](while-end-while-statement.md)
- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
