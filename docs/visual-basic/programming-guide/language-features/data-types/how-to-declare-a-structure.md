---
title: 'Procédure : Déclarer une structure'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: bffdc5974eff6b71e0abc4780a61aa300769eed6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058545"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Comment : déclarer une structure (Visual Basic)

Vous commencez une déclaration de structure par l' [instruction structure](../../../language-reference/statements/structure-statement.md)et vous la terminez par l' `End Structure` instruction. Entre ces deux instructions, vous devez déclarer au moins un *élément*. Les éléments peuvent être de n’importe quel type de données, mais au moins un doit être une variable non partagée ou un événement non personnalisé non partagé.  
  
 Vous ne pouvez pas initialiser l’un des éléments de structure dans la déclaration de structure. Quand vous déclarez une variable comme étant d’un type structure, vous assignez des valeurs aux éléments en y accédant via la variable.  
  
 Pour plus d’informations sur les différences entre les structures et les classes, consultez [structures et classes](structures-and-classes.md).  
  
 À des fins de démonstration, envisagez une situation dans laquelle vous souhaitez effectuer le suivi du nom, de l’extension téléphonique et du salaire d’un employé. Une structure vous permet d’effectuer cette opération dans une variable unique.  
  
### <a name="to-declare-a-structure"></a>Pour déclarer une structure  
  
1. Créez les instructions de début et de fin pour la structure.  
  
     Vous pouvez spécifier le niveau d’accès d’une structure à l’aide du mot clé [public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)ou [Private](../../../language-reference/modifiers/private.md) , ou vous pouvez laisser la valeur par défaut `Public` .  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Ajoutez des éléments au corps de la structure.  
  
     Une structure doit avoir au moins un élément. Vous devez déclarer chaque élément et spécifier un niveau d’accès pour celui-ci. Si vous utilisez l' [instruction Dim](../../../language-reference/statements/dim-statement.md) sans mot clé, l’accessibilité est par défaut `Public` .  
  
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
  
     Le `salary` champ dans l’exemple précédent est `Private` , ce qui signifie qu’il est inaccessible en dehors de la structure, même à partir de la classe conteneur. Toutefois, la `giveRaise` procédure est `Public` . elle peut donc être appelée à partir de l’extérieur de la structure. De même, vous pouvez déclencher l' `salaryReviewTime` événement à l’extérieur de la structure.  
  
     Outre les variables, `Sub` les procédures et les événements, vous pouvez également définir des constantes, des `Function` procédures et des propriétés dans une structure. Vous pouvez désigner au plus une propriété comme *propriété par défaut*, à condition qu’elle prenne au moins un argument. Vous pouvez gérer un événement avec une procédure [partagée](../../../language-reference/modifiers/shared.md) `Sub` . Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Voir aussi

- [Data types](index.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types de données composites](composite-data-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Structures](structures.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Variables de structure](structure-variables.md)
- [Structures et autres éléments de programmation](structures-and-other-programming-elements.md)
- [Structures et classes](structures-and-classes.md)
- [Type de données défini par l'utilisateur](../../../language-reference/data-types/user-defined-data-type.md)
