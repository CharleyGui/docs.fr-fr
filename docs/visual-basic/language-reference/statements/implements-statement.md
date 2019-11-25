---
title: Implements, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351152"
---
# <a name="implements-statement"></a>Implements, instruction
Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Composants  
 `interfacename`  
 Requis. An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.  
  
 `interfacemember`  
 Requis. The member of an interface that is being implemented.  
  
## <a name="remarks"></a>Notes  
 An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates. Interfaces contain only the declarations for members; classes and structures implement these members. Pour plus d’informations, consultez [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 The `Implements` statement must immediately follow the `Class` or `Structure` statement.  
  
 When you implement an interface, you must implement all the members declared in the interface. Omitting any member is considered to be a syntax error. To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure. Pour plus d’informations, consultez [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.  
  
## <a name="example"></a>Exemple  
 The following example shows how to use the `Implements` statement to implement members of an interface. It defines an interface named `ICustomerInfo` with an event, a property, and a procedure. The class `customerInfo` implements all the members defined in the interface.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface. Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.  
  
## <a name="example"></a>Exemple  
 The following two procedures show how you could use the interface implemented in the preceding example. To test the implementation, add these procedures to your project and call the `testImplements` procedure.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Voir aussi

- [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
