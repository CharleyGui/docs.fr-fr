---
title: 'Comment : déclarer une structure (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: c3090b5b8e53e5a5a990ae11c91464797bde9803
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582303"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Comment : déclarer une structure (Visual Basic)
Vous commencez une déclaration de structure par l' [instruction structure](../../../../visual-basic/language-reference/statements/structure-statement.md)et vous la terminez par l’instruction `End Structure`. Entre ces deux instructions, vous devez déclarer au moins un *élément*. Les éléments peuvent être de n’importe quel type de données, mais au moins un doit être une variable non partagée ou un événement non personnalisé non partagé.  
  
 Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure. Quand vous déclarez une variable comme étant d’un type structure, vous assignez des valeurs aux éléments en y accédant via la variable.  
  
 Pour plus d’informations sur les différences entre les structures et les classes, consultez [structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 À des fins de démonstration, envisagez une situation dans laquelle vous souhaitez effectuer le suivi du nom, de l’extension téléphonique et du salaire d’un employé. Une structure vous permet d’effectuer cette opération dans une variable unique.  
  
### <a name="to-declare-a-structure"></a>Pour déclarer une structure  
  
1. Créez les instructions de début et de fin pour la structure.  
  
     Vous pouvez spécifier le niveau d’accès d’une structure à l’aide du mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md), [protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../../visual-basic/language-reference/modifiers/private.md) , ou vous pouvez laisser la valeur par défaut `Public`.  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Ajoutez des éléments au corps de la structure.  
  
     Une structure doit avoir au moins un élément. Vous devez déclarer chaque élément et spécifier un niveau d’accès pour celui-ci. Si vous utilisez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sans mot clé, l’accessibilité a pour valeur par défaut `Public`.  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     Le champ `salary` dans l’exemple précédent est `Private`, ce qui signifie qu’il est inaccessible en dehors de la structure, même à partir de la classe conteneur. Toutefois, la procédure `giveRaise` est `Public` et peut donc être appelée à partir de l’extérieur de la structure. De même, vous pouvez déclencher l’événement `salaryReviewTime` à partir de l’extérieur de la structure.  
  
     En plus des variables, des procédures `Sub` et des événements, vous pouvez également définir des constantes, des procédures `Function` et des propriétés dans une structure. Vous pouvez désigner au plus une propriété comme *propriété par défaut*, à condition qu’elle prenne au moins un argument. Vous pouvez gérer un événement à l’aide d’une procédure de `Sub` [partagée](../../../../visual-basic/language-reference/modifiers/shared.md) . Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Variables de structure](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Type de données défini par l’utilisateur](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
