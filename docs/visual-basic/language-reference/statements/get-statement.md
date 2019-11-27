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
ms.openlocfilehash: 9560faf90d531c32f104dbd053a7c1f5584cfb1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351174"
---
# <a name="get-statement"></a>Get, instruction
Déclare une procédure de propriété `Get` utilisée pour récupérer la valeur d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Ce paramètre est facultatif. Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif sur au plus une des instructions `Get` et `Set` de cette propriété. Il peut s'agir de l'un des éléments suivants :<br /><br /> -   [protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Ce paramètre est facultatif. Une ou plusieurs instructions qui s’exécutent lorsque la procédure de propriété `Get` est appelée.|  
|`End Get`|Requis. Met fin à la définition de la procédure de propriété `Get`.|  
  
## <a name="remarks"></a>Notes  
 Chaque propriété doit avoir une procédure de propriété `Get`, sauf si la propriété est marquée comme `WriteOnly`. La procédure `Get` est utilisée pour retourner la valeur actuelle de la propriété.  
  
 Visual Basic appelle automatiquement la procédure `Get` d’une propriété lorsqu’une expression demande la valeur de la propriété.  
  
 Le corps de la déclaration de propriété peut contenir uniquement les procédures `Get` et `Set` de la propriété entre l' [instruction Property](../../../visual-basic/language-reference/statements/property-statement.md) et l’instruction `End Property`. Elle ne peut pas stocker d’autres éléments que ces procédures. En particulier, il ne peut pas stocker la valeur actuelle de la propriété. Vous devez stocker cette valeur en dehors de la propriété, car si vous la stockez à l’intérieur de l’une des procédures de propriété, l’autre procédure de propriété ne peut pas y accéder. L’approche habituelle consiste à stocker la valeur dans une variable [privée](../../../visual-basic/language-reference/modifiers/private.md) déclarée au même niveau que la propriété. Vous devez définir une procédure `Get` à l’intérieur de la propriété à laquelle elle s’applique.  
  
 La procédure `Get` a comme valeur par défaut le niveau d’accès de sa propriété conteneur, sauf si vous utilisez `accessmodifier` dans l’instruction `Get`.  
  
## <a name="rules"></a>Règles  
  
- **Niveaux d’accès mixtes.** Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour la `Get` ou la procédure `Set`, mais pas les deux. Dans ce cas, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété. Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer la procédure `Get` `Private`, mais pas `Public`.  
  
     Si vous définissez une propriété `ReadOnly`, la procédure `Get` représente la propriété entière. Vous ne pouvez pas déclarer un niveau d’accès différent pour `Get`, car cela aurait pour effet de définir deux niveaux d’accès pour la propriété.  
  
- **Type de retour.** L' [instruction Property](../../../visual-basic/language-reference/statements/property-statement.md) peut déclarer le type de données de la valeur qu’elle retourne. La procédure `Get` retourne automatiquement ce type de données. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface.  
  
     Si l’instruction `Property` ne spécifie pas `returntype`, la procédure retourne `Object`.  
  
## <a name="behavior"></a>Comportement  
  
- **Retour d’une procédure.** Lorsque la procédure `Get` retourne au code appelant, l’exécution continue dans l’instruction qui a demandé la valeur de la propriété.  
  
     `Get` procédures de propriété peuvent retourner une valeur à l’aide de l' [instruction return](../../../visual-basic/language-reference/statements/return-statement.md) ou en affectant la valeur de retour au nom de la propriété. Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Les instructions `Exit Property` et `Return` provoquent une sortie immédiate d’une procédure de propriété. Un nombre quelconque d’instructions `Exit Property` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Property` et `Return`.  
  
- **Valeur de retour.** Pour retourner une valeur à partir d’une procédure `Get`, vous pouvez affecter la valeur au nom de la propriété ou l’inclure dans une [instruction return](../../../visual-basic/language-reference/statements/return-statement.md). L’instruction `Return` assigne simultanément la valeur de retour de la procédure `Get` et quitte la procédure.  
  
     Si vous utilisez `Exit Property` sans assigner de valeur au nom de la propriété, la procédure `Get` retourne la valeur par défaut pour le type de données de la propriété. Pour plus d’informations, consultez « valeur de retour » dans l' [instruction de fonction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     L’exemple suivant illustre deux façons pour la propriété en lecture seule `quoteForTheDay` peut retourner la valeur contenue dans la variable privée `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Get` pour retourner la valeur d’une propriété.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Procédure pas à pas : définition de classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
