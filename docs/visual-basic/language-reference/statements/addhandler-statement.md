---
title: AddHandler, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004543"
---
# <a name="addhandler-statement"></a>AddHandler, instruction
Associe un événement à un gestionnaire d’événements au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Composants  
|||
|---|---|
|événement|Nom de l’événement à gérer.|  
|`eventhandler`|Nom d’une procédure qui gère l’événement.|
|||
  
## <a name="remarks"></a>Notes  
 Les instructions `AddHandler` et `RemoveHandler` vous permettent de démarrer et d’arrêter la gestion des événements à tout moment pendant l’exécution du programme.  
  
 La signature de la procédure `eventhandler` doit correspondre à la signature de l’événement `event`.  
  
 Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences. L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution. Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier. Pour plus d’informations, consultez [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Pour les événements personnalisés, l’instruction `AddHandler` appelle l’accesseur `AddHandler` de l’événement. Pour plus d’informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Voir aussi

- [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)
- [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
