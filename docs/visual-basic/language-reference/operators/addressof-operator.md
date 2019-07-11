---
title: Opérateur AddressOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760375"
---
# <a name="addressof-operator-visual-basic"></a>Opérateur AddressOf (Visual Basic)
Crée une instance de délégué qui fait référence à la procédure spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Composants  
 `procedurename`  
 Requis. Indique la procédure à référencer par le délégué nouvellement créé.  
  
## <a name="remarks"></a>Notes  
 Le `AddressOf` opérateur crée un délégué qui pointe vers le sub ou de la fonction spécifiée par `procedurename`. Lorsque la procédure spécifiée est qu'une méthode d’instance puis le délégué fait référence à l’instance et la méthode. Ensuite, lorsque le délégué est appelé la méthode spécifiée de l’instance spécifiée est appelée.  
  
 Le `AddressOf` opérateur peut être utilisé comme opérande d’un constructeur délégué ou il peut être utilisé dans un contexte dans lequel le type du délégué peut être déterminé par le compilateur.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `AddressOf` opérateur pour désigner un délégué pour gérer le `Click` événements d’un bouton.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `AddressOf` opérateur pour désigner la fonction de démarrage d’un thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
