---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349116"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Spécifie qu’un ou plusieurs éléments de programmation déclarés sont associés à une classe ou une structure au grand, et non à une instance spécifique de la classe ou de la structure.  
  
## <a name="remarks"></a>Notes  
  
## <a name="when-to-use-shared"></a>Quand utiliser le partagé  
 Le partage d’un membre d’une classe ou d’une structure le rend disponible pour chaque instance, plutôt que non *partagée*, où chaque instance conserve sa propre copie. Cela est utile, par exemple, si la valeur d’une variable s’applique à l’application entière. Si vous déclarez cette variable comme `Shared`, toutes les instances accèdent au même emplacement de stockage et si une instance modifie la valeur de la variable, toutes les instances accèdent à la valeur mise à jour.  
  
 Le partage ne modifie pas le niveau d’accès d’un membre. Par exemple, un membre de classe peut être partagé et privé (accessible uniquement à partir de la classe), ou non partagé et public. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `Shared` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un élément de `Shared` doit être une classe ou une structure, et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shared` avec [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)ou [static](../../../visual-basic/language-reference/modifiers/static.md) dans la même déclaration.  
  
- **L’accès à.** Vous accédez à un élément Shared en le qualifiant avec son nom de classe ou de structure, et non avec le nom de variable d’une instance spécifique de sa classe ou structure. Vous n’avez même pas besoin de créer une instance d’une classe ou d’une structure pour accéder à ses membres partagés.  
  
     L’exemple suivant appelle la procédure partagée <xref:System.Double.IsNaN%2A> exposée par la structure <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Partage implicite.** Vous ne pouvez pas utiliser le modificateur `Shared` dans une [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md), mais les constantes sont partagées implicitement. De même, vous ne pouvez pas déclarer un membre d’un module ou une interface à `Shared`, mais ils sont implicitement partagés.  
  
## <a name="behavior"></a>Comportement  
  
- **Rangement.** Une variable ou un événement partagé est stocké en mémoire une seule fois, quel que soit le nombre d’instances que vous créez de sa classe ou structure. De même, une procédure ou une propriété partagée ne contient qu’un seul jeu de variables locales.  
  
- **Accès par le biais d’une variable d’instance.** Il est possible d’accéder à un élément Shared en le qualifiant avec le nom d’une variable qui contient une instance spécifique de sa classe ou structure. Bien que cela fonctionne généralement comme prévu, le compilateur génère un message d’avertissement et donne l’accès par le biais du nom de la classe ou de la structure au lieu de la variable.  
  
- **Accès par le biais d’une expression d’instance.** Si vous accédez à un élément partagé par le biais d’une expression qui retourne une instance de sa classe ou structure, le compilateur effectue l’accès via le nom de la classe ou de la structure au lieu d’évaluer l’expression. Cela produit des résultats inattendus si vous avez souhaité que l’expression effectue d’autres actions et retourne l’instance. L’exemple suivant illustre ces actions.  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     Dans l’exemple précédent, le compilateur génère un message d’avertissement à la fois que le code accède à la variable partagée `total` via une instance. Dans chaque cas, il effectue l’accès directement par le biais de la classe `shareTotal` et n’utilise aucune instance. Dans le cas de l’appel prévu à la procédure `returnClass`, cela signifie qu’elle ne génère même pas d’appel à `returnClass`. par conséquent, l’action supplémentaire d’affichage de « Function returnClass () called » n’est pas effectuée.  
  
 Le modificateur `Shared` peut être utilisé dans les contextes suivants :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Durée de vie dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
