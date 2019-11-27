---
title: "Comment : contrôler la portée d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345374"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Comment : contrôler la portée d'une variable (Visual Basic)
Normalement, une variable est dans la *portée*, ou visible à des fins de référence, dans toute la région dans laquelle vous la déclarez. Dans certains cas, le niveau d' *accès* de la variable peut influencer son étendue.  
  
 Pour plus d'informations, consultez [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Portée au niveau du bloc ou de la procédure  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Pour rendre une variable visible uniquement dans un bloc  
  
- Placez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable entre les instructions de déclaration de début et de fin de ce bloc, par exemple entre les instructions `For` et `Next` d’une boucle `For`.  
  
     Vous ne pouvez faire référence à la variable qu’à partir du bloc.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Pour rendre une variable visible uniquement dans une procédure  
  
- Placez l’instruction `Dim` pour la variable à l’intérieur de la procédure, mais en dehors de tout bloc (par exemple, un bloc `With`...`End With`).  
  
     Vous ne pouvez faire référence à la variable qu’à partir de la procédure, y compris à l’intérieur de n’importe quel bloc contenu dans la procédure.  
  
## <a name="scope-at-module-or-namespace-level"></a>Portée au niveau du module ou de l’espace de noms  
 Pour plus de commodité, le *niveau de module* à simple terme s’applique de la même manière aux modules, aux classes et aux structures. Le niveau d’accès d’une variable de niveau module détermine sa portée. L’espace de noms qui contient le module, la classe ou la structure influence également la portée.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Pour rendre une variable visible dans l’ensemble d’un module, d’une classe ou d’une structure  
  
1. Placez l’instruction `Dim` pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l’instruction `Dim`.  
  
3. Vous pouvez faire référence à la variable depuis n’importe quel endroit du module, de la classe ou de la structure, mais pas à l’extérieur.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Pour rendre une variable visible dans l’ensemble d’un espace de noms  
  
1. Placez l’instruction `Dim` pour la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [public](../../../../visual-basic/language-reference/modifiers/public.md) dans l’instruction `Dim`.  
  
3. Vous pouvez faire référence à la variable depuis n’importe quel emplacement de l’espace de noms contenant le module, la classe ou la structure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare une variable au niveau du module et limite sa visibilité au code dans le module.  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 Dans l’exemple précédent, toutes les procédures définies dans le module `demonstrateScope` peuvent faire référence à la variable `String` `strMsg`. Lorsque la procédure `usePrivateVariable` est appelée, elle affiche le contenu de la variable de chaîne `strMsg` dans une boîte de dialogue.  
  
 Avec la modification suivante apporte à l’exemple précédent, la variable de chaîne `strMsg` peut être référencée par du code n’importe où dans l’espace de noms de sa déclaration.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Plus la portée d’une variable est restreinte, moins vous avez d’opportunités pour y faire référence par mégarde à la place d’une autre variable portant le même nom. Vous pouvez également réduire les problèmes de correspondance de référence.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Plus la portée d’une variable est restreinte, plus les probabilités de code malveillant peuvent être utilisées de manière incorrecte.  
  
## <a name="see-also"></a>Voir aussi

- [Étendue dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)
