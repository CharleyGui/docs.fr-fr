---
title: Inherits, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: e92e12908c89bb7a0bf385a2122b0c8f1eb8a6f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581753"
---
# <a name="inherits-statement"></a>Inherits Statement
Fait en sorte que la classe ou l’interface actuelle hérite des attributs, variables, propriétés, procédures et événements d’une autre classe ou d’un ensemble d’interfaces.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`basetypenames`|Requis. Nom de la classe dont cette classe est dérivée.<br /><br /> ou<br /><br /> Noms des interfaces à partir desquelles cette interface est dérivée. Utilisez des virgules pour séparer plusieurs noms.|  
  
## <a name="remarks"></a>Notes  
 En cas d’utilisation, l’instruction `Inherits` doit être la première ligne non vide et sans commentaire dans une définition de classe ou d’interface. Elle doit suivre immédiatement l’instruction `Class` ou `Interface`.  
  
 Vous pouvez utiliser `Inherits` uniquement dans une classe ou une interface. Cela signifie que le contexte de déclaration pour un héritage ne peut pas être un fichier source, un espace de noms, une structure, un module, une procédure ou un bloc.  
  
## <a name="rules"></a>Règles  
  
- **Héritage de classe.** Si une classe utilise l’instruction `Inherits`, vous ne pouvez spécifier qu’une seule classe de base.  
  
     Une classe ne peut pas hériter d’une classe imbriquée dans celle-ci.  
  
- **Héritage de l’interface.** Si une interface utilise l’instruction `Inherits`, vous pouvez spécifier une ou plusieurs interfaces de base. Vous pouvez hériter de deux interfaces, même si elles définissent un membre portant le même nom. Dans ce cas, le code d’implémentation doit utiliser la qualification de nom pour spécifier le membre qu’il implémente.  
  
     Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif. Par exemple, une interface de `Public` ne peut pas hériter d’une interface `Friend`.  
  
     Une interface ne peut pas hériter d’une interface imbriquée dans celle-ci.  
  
 Un exemple d’héritage de classe dans le .NET Framework est la classe <xref:System.ArgumentException>, qui hérite de la classe <xref:System.SystemException>. Cela permet d' <xref:System.ArgumentException> toutes les propriétés prédéfinies et les procédures requises par les exceptions système, telles que la propriété <xref:System.Exception.Message%2A> et la méthode <xref:System.Exception.ToString%2A>.  
  
 Un exemple d’héritage d’interface dans le .NET Framework est l’interface <xref:System.Collections.ICollection>, qui hérite de l’interface <xref:System.Collections.IEnumerable>. En conséquence, <xref:System.Collections.ICollection> hérite de la définition de l’énumérateur requis pour traverser une collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Inherits` pour montrer comment une classe nommée `thisClass` peut hériter de tous les membres d’une classe de base nommée `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’héritage de plusieurs interfaces.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 L’interface nommée `thisInterface` comprend désormais toutes les définitions des interfaces <xref:System.IComparable>, <xref:System.IDisposable> et <xref:System.IFormattable> que les membres hérités fournissent respectivement pour la comparaison spécifique au type de deux objets, la libération des ressources allouées et l’expression de la valeur de objet en tant que `String`. Une classe qui implémente `thisInterface` doit implémenter chaque membre de chaque interface de base.  
  
## <a name="see-also"></a>Voir aussi

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
