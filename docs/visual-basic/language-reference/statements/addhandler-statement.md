---
title: AddHandler, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 79dbe174209e91f13f5b43e8cdeb0b42edc4d163
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866711"
---
# <a name="addhandler-statement"></a>AddHandler, instruction

Associe un événement à un gestionnaire d’événements au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Éléments  

|||
|---|---|
|event|Nom de l’événement à gérer.|  
|`eventhandler`|Nom d’une procédure qui gère l’événement.|
|||
  
## <a name="remarks"></a>Notes  

 Les `AddHandler` `RemoveHandler` instructions et vous permettent de démarrer et d’arrêter la gestion des événements à tout moment pendant l’exécution du programme.  
  
 La signature de la `eventhandler` procédure doit correspondre à la signature de l’événement `event` .  
  
 Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences. L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution. Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier. Pour plus d’informations, consultez [Handles](handles-clause.md).  
  
> [!NOTE]
> Pour les événements personnalisés, l' `AddHandler` instruction appelle l’accesseur de l’événement `AddHandler` . Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](event-statement.md).  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [RemoveHandler, instruction](removehandler-statement.md)
- [Poignées](handles-clause.md)
- [Event, instruction](event-statement.md)
- [Événements](../../programming-guide/language-features/events/index.md)
