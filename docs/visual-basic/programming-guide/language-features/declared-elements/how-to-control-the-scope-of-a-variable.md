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
ms.openlocfilehash: 2ce7c1700eec54542719e6e0880466ca136e86f6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095431"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Comment : contrôler la portée d'une variable (Visual Basic)

Normalement, une variable est dans la *portée*, ou visible à des fins de référence, dans toute la région dans laquelle vous la déclarez. Dans certains cas, le niveau d' *accès* de la variable peut influencer son étendue.  
  
 Pour plus d'informations, consultez [Scope in Visual Basic](scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Portée au niveau du bloc ou de la procédure  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Pour rendre une variable visible uniquement dans un bloc  
  
- Placez l' [instruction Dim](../../../language-reference/statements/dim-statement.md) pour la variable entre les instructions de déclaration de début et de fin de ce bloc, par exemple entre `For` les `Next` instructions et d’une `For` boucle.  
  
     Vous ne pouvez faire référence à la variable qu’à partir du bloc.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Pour rendre une variable visible uniquement dans une procédure  
  
- Placez l' `Dim` instruction de la variable à l’intérieur de la procédure, mais en dehors de tout bloc (tel qu’un `With` bloc... `End With` ).  
  
     Vous ne pouvez faire référence à la variable qu’à partir de la procédure, y compris à l’intérieur de n’importe quel bloc contenu dans la procédure.  
  
## <a name="scope-at-module-or-namespace-level"></a>Portée au niveau du module ou de l’espace de noms  

 Pour plus de commodité, le *niveau de module* à simple terme s’applique de la même manière aux modules, aux classes et aux structures. Le niveau d’accès d’une variable de niveau module détermine sa portée. L’espace de noms qui contient le module, la classe ou la structure influence également la portée.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Pour rendre une variable visible dans l’ensemble d’un module, d’une classe ou d’une structure  
  
1. Placez l' `Dim` instruction de la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [Private](../../../language-reference/modifiers/private.md) dans l' `Dim` instruction.  
  
3. Vous pouvez faire référence à la variable depuis n’importe quel endroit du module, de la classe ou de la structure, mais pas à l’extérieur.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Pour rendre une variable visible dans l’ensemble d’un espace de noms  
  
1. Placez l' `Dim` instruction de la variable à l’intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2. Incluez le mot clé [Friend](../../../language-reference/modifiers/friend.md) ou [public](../../../language-reference/modifiers/public.md) dans l' `Dim` instruction.  
  
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
  
 Dans l’exemple précédent, toutes les procédures définies dans le module `demonstrateScope` peuvent faire référence à la `String` variable `strMsg` . Lorsque la `usePrivateVariable` procédure est appelée, elle affiche le contenu de la variable de chaîne `strMsg` dans une boîte de dialogue.  
  
 Avec la modification suivante apporte à l’exemple précédent, la variable de chaîne `strMsg` peut être référencée par du code n’importe où dans l’espace de noms de sa déclaration.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Programmation fiable  

 Plus la portée d’une variable est restreinte, moins vous avez d’opportunités pour y faire référence par mégarde à la place d’une autre variable portant le même nom. Vous pouvez également réduire les problèmes de correspondance de référence.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Plus la portée d’une variable est restreinte, plus les probabilités de code malveillant peuvent être utilisées de manière incorrecte.  
  
## <a name="see-also"></a>Voir aussi

- [Portée dans Visual Basic](scope.md)
- [Durée de vie dans Visual Basic](lifetime.md)
- [Niveaux d’accès dans Visual Basic](access-levels.md)
- [Variables](../variables/index.md)
- [Déclaration de variable](../variables/variable-declaration.md)
- [Dim (instruction)](../../../language-reference/statements/dim-statement.md)
