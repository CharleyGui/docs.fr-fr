---
title: Get, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 3da6c099b3f43a144484eaddf58605609eb0bbfe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866203"
---
# <a name="get-statement"></a>Get, instruction

Déclare une `Get` procédure de propriété utilisée pour récupérer la valeur d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Optionnel. Consultez la [liste des attributs](attribute-list.md).|  
|`accessmodifier`|Facultatif sur au plus une des `Get` instructions et `Set` dans cette propriété. Il peut s'agir d'une des méthodes suivantes :<br /><br /> -   [Protect](../modifiers/protected.md)<br />-   [Contact](../modifiers/friend.md)<br />-   [Priv](../modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Optionnel. Une ou plusieurs instructions qui s’exécutent lorsque la `Get` procédure de propriété est appelée.|  
|`End Get`|Obligatoire. Met fin à la définition de la `Get` procédure de propriété.|  
  
## <a name="remarks"></a>Notes  

 Chaque propriété doit avoir une `Get` procédure de propriété, sauf si la propriété est marquée `WriteOnly` . La `Get` procédure est utilisée pour retourner la valeur actuelle de la propriété.  
  
 Visual Basic appelle automatiquement la procédure d’une propriété `Get` lorsqu’une expression demande la valeur de la propriété.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures et de la propriété `Get` `Set` entre l' [instruction Property](property-statement.md) et l' `End Property` instruction. Elle ne peut pas stocker d’autres éléments que ces procédures. En particulier, il ne peut pas stocker la valeur actuelle de la propriété. Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder. L’approche habituelle consiste à stocker la valeur dans une variable [privée](../modifiers/private.md) déclarée au même niveau que la propriété. Vous devez définir une `Get` procédure à l’intérieur de la propriété à laquelle elle s’applique.  
  
 La `Get` procédure utilise par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l' `Get` instruction.  
  
## <a name="rules"></a>Règles  
  
- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` `Set` procédure ou, mais pas pour les deux. Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend` , vous pouvez déclarer la `Get` procédure `Private` , mais pas `Public` .  
  
     Si vous définissez une `ReadOnly` propriété, la `Get` procédure représente la propriété entière. Vous ne pouvez pas déclarer un niveau d’accès différent pour `Get` , car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.  
  
- **Type de retour.** L' [instruction Property](property-statement.md) peut déclarer le type de données de la valeur qu’elle retourne. La `Get` procédure retourne automatiquement ce type de données. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.  
  
     Si l' `Property` instruction ne spécifie pas `returntype` , la procédure retourne `Object` .  
  
## <a name="behavior"></a>Comportement  
  
- **Retour d’une procédure.** Lorsque la `Get` procédure revient au code appelant, l’exécution continue dans l’instruction qui a demandé la valeur de la propriété.  
  
     `Get` les procédures de propriété peuvent retourner une valeur à l’aide de l' [instruction return](return-statement.md) ou en affectant la valeur de retour au nom de la propriété. Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](function-statement.md).  
  
     Les `Exit Property` `Return` instructions et provoquent une sortie immédiate d’une procédure de propriété. Un nombre quelconque `Exit Property` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Property` `Return` instructions et.  
  
- **Valeur de retour.** Pour retourner une valeur à partir d’une `Get` procédure, vous pouvez affecter la valeur au nom de la propriété ou l’inclure dans une [instruction return](return-statement.md). L' `Return` instruction assigne simultanément la `Get` valeur de retour de la procédure et quitte la procédure.  
  
     Si vous utilisez `Exit Property` sans assigner de valeur au nom de la propriété, la `Get` procédure retourne la valeur par défaut pour le type de données de la propriété. Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](function-statement.md).  
  
     L’exemple suivant illustre deux façons dont la propriété en lecture seule `quoteForTheDay` peut retourner la valeur contenue dans la variable privée `quoteValue` .  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `Get` instruction pour retourner la valeur d’une propriété.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- [Instruction Set](set-statement.md)
- [Property Statement](property-statement.md)
- [Exit (instruction)](exit-statement.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Procédure pas à pas : définition de classes](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
