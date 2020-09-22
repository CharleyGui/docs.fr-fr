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
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873243"
---
# <a name="implements-statement"></a>Implements, instruction

Spécifie une ou plusieurs interfaces, ou membres d’interface, qui doivent être implémentées dans la définition de la classe ou de la structure dans laquelle elles apparaissent.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Éléments  

 `interfacename`  
 Obligatoire. Interface dont les propriétés, les procédures et les événements doivent être implémentés par les membres correspondants dans la classe ou la structure.  
  
 `interfacemember`  
 Obligatoire. Membre d’une interface qui est implémentée.  
  
## <a name="remarks"></a>Notes  

 Une interface est une collection de prototypes représentant les membres (propriétés, procédures et événements) encapsulés par l’interface. Les interfaces contiennent uniquement les déclarations pour les membres ; les classes et les structures implémentent ces membres. Pour plus d'informations, consultez [Interfaces](../../programming-guide/language-features/interfaces/index.md).  
  
 L' `Implements` instruction doit suivre immédiatement l' `Class` `Structure` instruction ou.  
  
 Lorsque vous implémentez une interface, vous devez implémenter tous les membres déclarés dans l’interface. L’omission d’un membre est considérée comme une erreur de syntaxe. Pour implémenter un membre individuel, vous spécifiez le mot clé [Implements](implements-clause.md) (qui est distinct de l' `Implements` instruction) lorsque vous déclarez le membre dans la classe ou la structure. Pour plus d'informations, consultez [Interfaces](../../programming-guide/language-features/interfaces/index.md).  
  
 Les classes peuvent utiliser des implémentations [privées](../modifiers/private.md) de propriétés et de procédures, mais ces membres sont accessibles uniquement en effectuant un cast d’une instance de la classe d’implémentation dans une variable déclarée comme étant du type de l’interface.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment utiliser l' `Implements` instruction pour implémenter des membres d’une interface. Il définit une interface nommée `ICustomerInfo` avec un événement, une propriété et une procédure. La classe `customerInfo` implémente tous les membres définis dans l’interface.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Notez que la classe `customerInfo` utilise l' `Implements` instruction sur une ligne de code source distincte pour indiquer que la classe implémente tous les membres de l' `ICustomerInfo` interface. Ensuite, chaque membre de la classe utilise le `Implements` mot clé dans le cadre de sa déclaration de membre pour indiquer qu’il implémente ce membre d’interface.  
  
## <a name="example"></a>Exemple  

 Les deux procédures suivantes montrent comment utiliser l’interface implémentée dans l’exemple précédent. Pour tester l’implémentation, ajoutez ces procédures à votre projet et appelez la `testImplements` procédure.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Voir aussi

- [Implémente](implements-clause.md)
- [Interface (instruction)](interface-statement.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
