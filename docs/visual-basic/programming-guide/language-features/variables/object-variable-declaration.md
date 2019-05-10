---
title: Déclaration des variables objets (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 9e57d49965537a45bc62b9078079389efcfb2e2c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598745"
---
# <a name="object-variable-declaration-visual-basic"></a>Déclaration des variables objets (Visual Basic)
Vous utilisez une instruction de déclaration normale pour déclarer une variable objet. Pour le type de données, vous spécifiez `Object` (autrement dit, le [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) ou une classe plus spécifique à partir duquel l’objet doit être créé.  
  
 Déclaration d’une variable en tant que `Object` est identique à la déclarer comme <xref:System.Object?displayProperty=nameWithType>.  
  
 Lorsque vous déclarez une variable avec une classe d’objet spécifique, il peut accéder à toutes les méthodes et propriétés exposées par cette classe et les classes dont elle hérite. Si vous déclarez la variable avec <xref:System.Object>, il peut accéder uniquement aux membres de la <xref:System.Object> classe, sauf si vous activez `Option Strict Off` pour permettre la liaison tardive.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 Pour déclarer une variable objet, utilisez la syntaxe suivante :  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Vous pouvez également spécifier [Public](../../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privé](../../../../visual-basic/language-reference/modifiers/private.md), [partagé](../../../../visual-basic/language-reference/modifiers/shared.md), ou [statique](../../../../visual-basic/language-reference/modifiers/static.md) dans la déclaration. Les exemples de déclarations suivantes sont valides :  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Liaison tardive et à liaison anticipée  
 Parfois, la classe spécifique est inconnue jusqu'à ce que votre code s’exécute. Dans ce cas, vous devez déclarer la variable objet avec le `Object` type de données. Cette opération crée une référence générale à tout type d’objet, et la classe spécifique est affectée au moment de l’exécution. Il s’agit *liaison tardive*. Liaison tardive nécessite plus de temps d’exécution. Il limite également votre code aux méthodes et propriétés de la classe que vous avez récemment affecté à ce dernier. Cela peut provoquer des erreurs d’exécution si votre code tente d’accéder aux membres de classe différente.  
  
 Lorsque vous connaissez la classe spécifique au moment de la compilation, vous devez déclarer la variable objet comme étant de cette classe. Il s’agit de la *liaison anticipée*. Liaison anticipée améliore les performances et garantit votre code d’accéder à toutes les méthodes et propriétés de la classe spécifique. Dans les exemples de déclarations précédents, si la variable `objA` utilise uniquement les objets de la classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, vous devez spécifier `As System.Windows.Forms.Label` dans sa déclaration.  
  
### <a name="advantages-of-early-binding"></a>Avantages de la liaison anticipée  
 Déclarez une variable objet comme une classe spécifique présente plusieurs avantages :  
  
- La vérification de type automatique  
  
- La garantie d’accéder à tous les membres de la classe spécifique  
  
- Prise en charge de Microsoft IntelliSense dans l’éditeur de Code  
  
- Une meilleure lisibilité de votre code  
  
- Moins d’erreurs dans votre code  
  
- Les erreurs interceptées au moment de la compilation plutôt que durée d’exécution  
  
- Exécution de code plus rapide  
  
## <a name="access-to-object-variable-members"></a>Accès aux membres des variables objets  
 Lorsque `Option Strict` est activé `On`, une variable objet peut accéder qu’aux méthodes et propriétés de la classe avec laquelle vous la déclarez. L'exemple suivant illustre ce comportement.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la <xref:System.Object> classe proprement dite, qui n’incluent pas la propriété `Left` . En revanche, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>. Il peut donc utiliser toutes les méthodes et propriétés de la classe <xref:System.Windows.Forms.Label> dans l’espace de noms <xref:System.Windows.Forms> .  
  
## <a name="flexibility-of-object-variables"></a>Flexibilité des Variables objets  
 Lorsque vous travaillez avec des objets dans une hiérarchie d’héritage, vous avez le choix de la classe à utiliser pour déclarer vos variables d’objet. Lors de ce choix, vous devez comparer la flexibilité d’attribution de l’objet contre tout accès aux membres d’une classe. Par exemple, considérez la hiérarchie d’héritage qui mène à la <xref:System.Windows.Forms.Form?displayProperty=nameWithType> classe :  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Supposons que votre application définit une classe de formulaire appelée `specialForm`, qui hérite de la classe <xref:System.Windows.Forms.Form>. Vous pouvez déclarer une variable objet qui fait référence à `specialForm`, comme illustré dans l’exemple suivant.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 La déclaration dans l’exemple précédent limite la variable `nextForm` vers des objets de classe `specialForm`, mais il permet aussi de toutes les méthodes et propriétés de `specialForm` disponibles pour `nextForm`, ainsi que tous les membres de toutes les classes à partir de laquelle `specialForm` hérite.  
  
 Vous pouvez rendre une variable objet plus générale en déclarant qu’elle soit de type <xref:System.Windows.Forms.Form>, comme illustré dans l’exemple suivant.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 La déclaration dans l’exemple précédent vous permet d’affecter n’importe quel formulaire de votre application à `anyForm`. Toutefois, bien que `anyForm` peut accéder à tous les membres de classe <xref:System.Windows.Forms.Form>, il ne peut pas utiliser toutes les méthodes ou propriétés supplémentaires définies pour les formulaires spécifiques comme `specialForm`.  
  
 Tous les membres de classe de base sont disponibles pour les classes dérivées, mais les membres supplémentaires d’une classe dérivée ne sont pas disponibles pour la classe de base.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Assignation des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Guide pratique pour Déclarer une Variable objet et lui assigner un objet en Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Guide pratique pour Accéder aux membres d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New (opérateur)](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
