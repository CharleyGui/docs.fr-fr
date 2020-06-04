---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404497"
---
# <a name="inherits-statement"></a>Inherits Statement
Fait en sorte que la classe ou l’interface actuelle hérite des attributs, variables, propriétés, procédures et événements d’une autre classe ou d’un ensemble d’interfaces.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`basetypenames`|Obligatoire. Nom de la classe dont cette classe est dérivée.<br /><br /> -ou-<br /><br /> Noms des interfaces à partir desquelles cette interface est dérivée. Utilisez des virgules pour séparer plusieurs noms.|  
  
## <a name="remarks"></a>Notes  
 Si elle est utilisée, l' `Inherits` instruction doit être la première ligne non vide et sans commentaire dans une définition de classe ou d’interface. Elle doit suivre immédiatement l' `Class` `Interface` instruction ou.  
  
 Vous pouvez utiliser `Inherits` uniquement dans une classe ou une interface. Cela signifie que le contexte de déclaration pour un héritage ne peut pas être un fichier source, un espace de noms, une structure, un module, une procédure ou un bloc.  
  
## <a name="rules"></a>Règles  
  
- **Héritage de classe.** Si une classe utilise l' `Inherits` instruction, vous ne pouvez spécifier qu’une seule classe de base.  
  
     Une classe ne peut pas hériter d’une classe imbriquée dans celle-ci.  
  
- **Héritage de l’interface.** Si une interface utilise l' `Inherits` instruction, vous pouvez spécifier une ou plusieurs interfaces de base. Vous pouvez hériter de deux interfaces, même si elles définissent un membre portant le même nom. Dans ce cas, le code d’implémentation doit utiliser la qualification de nom pour spécifier le membre qu’il implémente.  
  
     Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif. Par exemple, une `Public` interface ne peut pas hériter d’une `Friend` interface.  
  
     Une interface ne peut pas hériter d’une interface imbriquée dans celle-ci.  
  
 Un exemple d’héritage de classe dans le .NET Framework est la <xref:System.ArgumentException> classe, qui hérite de la <xref:System.SystemException> classe. Cela fournit <xref:System.ArgumentException> toutes les propriétés prédéfinies et les procédures requises par les exceptions système, telles que la <xref:System.Exception.Message%2A> propriété et la <xref:System.Exception.ToString%2A> méthode.  
  
 Un exemple d’héritage d’interface dans le .NET Framework est l' <xref:System.Collections.ICollection> interface, qui hérite de l' <xref:System.Collections.IEnumerable> interface. Cela a <xref:System.Collections.ICollection> pour effet d’hériter de la définition de l’énumérateur requis pour parcourir une collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Inherits` instruction pour montrer comment une classe nommée `thisClass` peut hériter de tous les membres d’une classe de base nommée `anotherClass` .  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’héritage de plusieurs interfaces.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 L’interface nommée `thisInterface` contient désormais toutes les définitions des <xref:System.IComparable> interfaces, <xref:System.IDisposable> et <xref:System.IFormattable> que les membres hérités fournissent respectivement pour la comparaison spécifique au type de deux objets, la libération des ressources allouées et l’expression de la valeur d’un objet sous la forme d’un `String` . Une classe qui implémente `thisInterface` doit implémenter chaque membre de chaque interface de base.  
  
## <a name="see-also"></a>Voir aussi

- [MustInherit](../modifiers/mustinherit.md)
- [NotInheritable](../modifiers/notinheritable.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
