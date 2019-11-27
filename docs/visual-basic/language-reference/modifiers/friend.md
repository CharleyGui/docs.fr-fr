---
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351560"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de l’assembly qui contient leur déclaration.  
  
## <a name="remarks"></a>Notes  
 Dans de nombreux cas, vous souhaitez que les éléments de programmation tels que les classes et les structures soient utilisés par l’assembly entier, non seulement par le composant qui les déclare. Toutefois, vous ne voudrez peut-être pas qu’elles soient accessibles par du code en dehors de l’assembly (par exemple, si l’application est propriétaire). Si vous souhaitez limiter l’accès à un élément de cette manière, vous pouvez le déclarer à l’aide du modificateur `Friend`.  
  
 Du code dans d’autres classes, structures et modules compilés dans le même assembly peut accéder à tous les éléments `Friend` de cet assembly.  
  
 `Friend` accès est souvent le niveau préféré pour les éléments de programmation d’une application, et `Friend` est le niveau d’accès par défaut d’une interface, d’un module, d’une classe ou d’une structure.  
  
 Vous pouvez utiliser `Friend` uniquement au niveau du module, de l’interface ou de l’espace de noms. Par conséquent, le contexte de déclaration pour un élément `Friend` doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure ; il ne peut pas s’agir d’une procédure.  

> [!NOTE]
> Vous pouvez également utiliser le modificateur d’accès [Protected Friend](protected-friend.md) , qui rend un membre de classe accessible à partir de cette classe, des classes dérivées et du même assembly dans lequel la classe est définie. Pour restreindre l’accès à un membre à partir de sa classe et à partir de classes dérivées dans le même assembly, vous utilisez le modificateur d’accès [protected Private](private-protected.md) .

 Pour une comparaison des `Friend` et des autres modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Vous pouvez spécifier qu’un autre assembly est un assembly friend, ce qui lui permet d’accéder à tous les types et membres marqués comme `Friend`. Pour plus d’informations, consultez [Assemblys friend](../../../standard/assembly/friend.md).

## <a name="example"></a>Exemple  
 La classe suivante utilise le modificateur `Friend` pour permettre à d’autres éléments de programmation dans le même assembly d’accéder à certains membres.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Utilisation  
 Vous pouvez utiliser le modificateur `Friend` dans ces contextes :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
