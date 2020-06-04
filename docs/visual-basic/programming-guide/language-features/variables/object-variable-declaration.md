---
title: Déclaration des variables objets
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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410359"
---
# <a name="object-variable-declaration-visual-basic"></a>Déclaration des variables objets (Visual Basic)
Vous utilisez une instruction de déclaration normale pour déclarer une variable objet. Pour le type de données, vous spécifiez `Object` (autrement dit, le [type de données Object](../../../language-reference/data-types/object-data-type.md)) ou une classe plus spécifique à partir de laquelle l’objet doit être créé.  
  
 La déclaration d’une variable comme `Object` revient à la déclarer comme <xref:System.Object?displayProperty=nameWithType> .  
  
 Quand vous déclarez une variable avec une classe d’objet spécifique, elle peut accéder à toutes les méthodes et propriétés exposées par cette classe et les classes dont elle hérite. Si vous déclarez la variable avec <xref:System.Object> , elle ne peut accéder qu’aux membres de la <xref:System.Object> classe, sauf si vous activez la `Option Strict Off` liaison tardive.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 Pour déclarer une variable objet, utilisez la syntaxe ci-après :  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Vous pouvez également spécifier [public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend` , [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md)ou [static](../../../language-reference/modifiers/static.md) dans la déclaration. Les exemples de déclarations suivants sont valides :  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Liaison tardive et liaison précoce  
 Parfois, la classe spécifique est inconnue jusqu’à ce que votre code s’exécute. Dans ce cas, vous devez déclarer la variable objet avec le `Object` type de données. Cela crée une référence générale à tout type d’objet, et la classe spécifique est assignée au moment de l’exécution. C’est ce que l’on appelle la *liaison tardive*. La liaison tardive requiert une durée d’exécution supplémentaire. Il limite également votre code aux méthodes et aux propriétés de la classe que vous avez récemment assignée. Cela peut provoquer des erreurs au moment de l’exécution si votre code tente d’accéder aux membres d’une classe différente.  
  
 Lorsque vous connaissez la classe spécifique au moment de la compilation, vous devez déclarer la variable objet comme étant de cette classe. Il s’agit de la *liaison anticipée*. La liaison précoce améliore les performances et garantit que votre code accède à toutes les méthodes et propriétés de la classe spécifique. Dans les exemples de déclarations précédents, si la variable `objA` utilise uniquement des objets de classe <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , vous devez spécifier `As System.Windows.Forms.Label` dans sa déclaration.  
  
### <a name="advantages-of-early-binding"></a>Avantages de la liaison anticipée  
 La déclaration d’une variable objet en tant que classe spécifique vous offre plusieurs avantages :  
  
- Vérification automatique des types  
  
- Accès garanti à tous les membres de la classe spécifique  
  
- Prise en charge de Microsoft IntelliSense dans l’éditeur de code  
  
- Amélioration de la lisibilité de votre code  
  
- Moins d’erreurs dans votre code  
  
- Erreurs détectées au moment de la compilation plutôt qu’au moment de l’exécution  
  
- Exécution de code plus rapide  
  
## <a name="access-to-object-variable-members"></a>Accès aux membres d’une variable objet  
 Lorsque `Option Strict` est activé `On` , une variable objet peut accéder uniquement aux méthodes et aux propriétés de la classe avec laquelle vous la déclarez. L'exemple suivant illustre ce comportement.  
  
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
  
## <a name="flexibility-of-object-variables"></a>Flexibilité des variables d’objet  
 Lorsque vous utilisez des objets dans une hiérarchie d’héritage, vous avez le choix de la classe à utiliser pour déclarer vos variables d’objet. Dans ce choix, vous devez équilibrer la flexibilité de l’assignation d’objet par rapport à l’accès aux membres d’une classe. Par exemple, considérez la hiérarchie d’héritage qui amène à la <xref:System.Windows.Forms.Form?displayProperty=nameWithType> classe :  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Supposons que votre application définit une classe de formulaire appelée `specialForm` , qui hérite de la classe <xref:System.Windows.Forms.Form> . Vous pouvez déclarer une variable objet qui fait référence spécifiquement à `specialForm` , comme le montre l’exemple suivant.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 La déclaration de l’exemple précédent limite la variable `nextForm` aux objets de la classe `specialForm` , mais elle rend également toutes les méthodes et propriétés de `specialForm` disponibles pour `nextForm` , ainsi que tous les membres de toutes les classes dont `specialForm` hérite.  
  
 Vous pouvez rendre une variable objet plus générale en la déclarant comme étant de type <xref:System.Windows.Forms.Form> , comme le montre l’exemple suivant.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 La déclaration de l’exemple précédent vous permet d’assigner n’importe quel formulaire dans votre application à `anyForm` . Toutefois, même si `anyForm` peut accéder à tous les membres de la classe <xref:System.Windows.Forms.Form> , il ne peut pas utiliser les méthodes ou propriétés supplémentaires définies pour des formulaires spécifiques tels que `specialForm` .  
  
 Tous les membres d’une classe de base sont disponibles pour les classes dérivées, mais les membres supplémentaires d’une classe dérivée ne sont pas disponibles pour la classe de base.  
  
## <a name="see-also"></a>Voir aussi

- [Variables objets](object-variables.md)
- [Affectation des variables objets](object-variable-assignment.md)
- [Valeurs des variables objets](object-variable-values.md)
- [Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Guide pratique : accéder aux membres d’un objet](how-to-access-members-of-an-object.md)
- [Nouvel opérateur](../../../language-reference/operators/new-operator.md)
- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
- [Inférence de type local](local-type-inference.md)
