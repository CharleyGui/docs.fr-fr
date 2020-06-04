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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404250"
---
# <a name="removehandler-statement"></a>RemoveHandler, instruction
Supprime l’association entre un événement et un gestionnaire d’événements.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`event`|Nom de l’événement géré.|  
|`eventhandler`|Nom de la procédure qui gère actuellement l’événement.|  
  
## <a name="remarks"></a>Notes  
 Les `AddHandler` `RemoveHandler` instructions et vous permettent de démarrer et d’arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.  
  
> [!NOTE]
> Pour les événements personnalisés, l' `RemoveHandler` instruction appelle l’accesseur de l’événement `RemoveHandler` . Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [AddHandler, instruction](addhandler-statement.md)
- [Poignées](handles-clause.md)
- [Event, instruction](event-statement.md)
- [Événements](../../programming-guide/language-features/events/index.md)
