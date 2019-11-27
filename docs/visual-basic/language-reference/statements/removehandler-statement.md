---
title: RemoveHandler, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 177952acf362ccb36a36b5f09b11a1a93dbefa29
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333036"
---
# <a name="removehandler-statement"></a>RemoveHandler, instruction
Supprime l’association entre un événement et un gestionnaire d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`event`|Nom de l’événement géré.|  
|`eventhandler`|Nom de la procédure qui gère actuellement l’événement.|  
  
## <a name="remarks"></a>Notes  
 Les instructions `AddHandler` et `RemoveHandler` vous permettent de démarrer et d’arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.  
  
> [!NOTE]
> Pour les événements personnalisés, l’instruction `RemoveHandler` appelle l’accesseur `RemoveHandler` de l’événement. Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [AddHandler (instruction)](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)
- [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
