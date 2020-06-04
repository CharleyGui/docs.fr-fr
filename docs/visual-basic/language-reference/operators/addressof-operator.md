---
title: AddressOf, opérateur
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372062"
---
# <a name="addressof-operator-visual-basic"></a>Opérateur AddressOf (Visual Basic)
Crée une instance de délégué qui fait référence à la procédure spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Éléments  
 `procedurename`  
 Obligatoire. Spécifie la procédure à référencer par le délégué nouvellement créé.  
  
## <a name="remarks"></a>Notes  
 L' `AddressOf` opérateur crée un délégué qui pointe vers la sous ou la fonction spécifiée par `procedurename` . Lorsque la procédure spécifiée est une méthode d’instance, le délégué fait référence à la fois à l’instance et à la méthode. Ensuite, lorsque le délégué est appelé, la méthode spécifiée de l’instance spécifiée est appelée.  
  
 L' `AddressOf` opérateur peut être utilisé comme opérande d’un constructeur délégué ou il peut être utilisé dans un contexte dans lequel le type du délégué peut être déterminé par le compilateur.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l' `AddressOf` opérateur pour désigner un délégué pour gérer l' `Click` événement d’un bouton.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `AddressOf` opérateur pour désigner la fonction de démarrage d’un thread.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Declare Statement](../statements/declare-statement.md)
- [Function (instruction)](../statements/function-statement.md)
- [Sub (instruction)](../statements/sub-statement.md)
- [Délégués](../../programming-guide/language-features/delegates/index.md)
