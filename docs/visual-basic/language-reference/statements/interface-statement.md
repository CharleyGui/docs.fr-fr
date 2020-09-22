---
title: Interface (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 3025adfe8c881a08df3b5f03253510c263c624d1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873228"
---
# <a name="interface-statement-visual-basic"></a>Interface, instruction (Visual Basic)

Déclare le nom d’une interface et introduit les définitions des membres que l’interface comprend.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Optionnel. Consultez la [liste des attributs](attribute-list.md).|  
|`accessmodifier`|Optionnel. Il peut s'agir d'une des méthodes suivantes :<br /><br /> -   [Publique](../modifiers/public.md)<br />-   [Protect](../modifiers/protected.md)<br />-   [Contact](../modifiers/friend.md)<br />-   [Priv](../modifiers/private.md)<br />-  [Ami protégé](../modifiers/protected-friend.md)<br/>- [Protégé privé](../modifiers/private-protected.md)<br /><br /> Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Optionnel. Consultez [Shadows](../modifiers/shadows.md).|  
|`name`|Obligatoire. Nom de cette interface. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Optionnel. Spécifie qu’il s’agit d’une interface générique.|  
|`typelist`|Obligatoire si vous utilisez le mot clé [of](of-clause.md) . Liste des paramètres de type pour cette interface. Éventuellement, chaque paramètre de type peut être déclaré variant à l’aide `In` des `Out` modificateurs génériques et. Consultez la [liste des types](type-list.md).|  
|`Inherits`|Optionnel. Indique que cette interface hérite des attributs et des membres d’une autre interface ou d’interfaces. Consultez [Inherits (instruction](inherits-statement.md)).|  
|`interfacenames`|Obligatoire si vous utilisez l' `Inherits` instruction. Noms des interfaces à partir desquelles cette interface est dérivée.|  
|`modifiers`|Optionnel. Modificateurs appropriés pour le membre d’interface qui est défini.|  
|`Property`|Optionnel. Définit une propriété qui est un membre de l’interface.|  
|`Function`|Optionnel. Définit une `Function` procédure qui est un membre de l’interface.|  
|`Sub`|Optionnel. Définit une `Sub` procédure qui est un membre de l’interface.|  
|`Event`|Optionnel. Définit un événement qui est membre de l’interface.|  
|`Interface`|Optionnel. Définit une interface qui est imbriquée dans cette interface. La définition de l’interface imbriquée doit se terminer par une `End Interface` instruction.|  
|`Class`|Optionnel. Définit une classe qui est un membre de l’interface. La définition de la classe membre doit se terminer par une `End Class` instruction.|  
|`Structure`|Optionnel. Définit une structure qui est un membre de l’interface. La définition de la structure du membre doit se terminer par une `End Structure` instruction.|  
|`membername`|Obligatoire pour chaque propriété, procédure, événement, interface, classe ou structure définie en tant que membre de l’interface. Nom du membre.|  
|`End Interface`|Met fin à la `Interface` définition.|  
  
## <a name="remarks"></a>Notes  

 Une *interface* définit un ensemble de membres, tels que des propriétés et des procédures, que les classes et les structures peuvent implémenter. L’interface définit uniquement les signatures des membres et non leurs mécanismes internes.  
  
 Une classe ou une structure implémente l’interface en fournissant du code pour chaque membre défini par l’interface. Enfin, lorsque l’application crée une instance à partir de cette classe ou de cette structure, un objet existe et s’exécute en mémoire. Pour plus d’informations, consultez [objets et classes](../../programming-guide/language-features/objects-and-classes/index.md) et [interfaces](../../programming-guide/language-features/interfaces/index.md).  
  
 Vous pouvez utiliser `Interface` uniquement au niveau de l’espace de noms ou du module. Cela signifie que le *contexte de déclaration* pour une interface doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).  
  
 Par défaut, les interfaces accèdent à [Friend](../modifiers/friend.md) . Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
- **Interfaces d’imbrication.** Vous pouvez définir une interface dans une autre. L’interface externe est appelée *interface conteneur*et l’interface interne est appelée *interface imbriquée*.  
  
- **Déclaration de membre.** Quand vous déclarez une propriété ou une procédure en tant que membre d’une interface, vous définissez uniquement la *signature* de cette propriété ou procédure. Cela comprend le type d’élément (propriété ou procédure), ses paramètres et ses types de paramètres, ainsi que son type de retour. Pour cette raison, la définition de membre n’utilise qu’une seule ligne de code et les instructions de fin telles que `End Function` ou ne `End Property` sont pas valides dans une interface.  
  
     En revanche, lorsque vous définissez une énumération ou une structure, ou une classe ou une interface imbriquée, il est nécessaire d’inclure leurs membres de données.  
  
- **Modificateurs de membre.** Vous ne pouvez pas utiliser de modificateurs d’accès lorsque vous définissez des membres de module, ni spécifier [Shared](../modifiers/shared.md) ou un modificateur de procédure à l’exception des [surcharges](../modifiers/overloads.md). Vous pouvez déclarer n’importe quel membre avec des [ombres](../modifiers/shadows.md), et vous pouvez utiliser la [valeur par défaut](../modifiers/default.md) lors de la définition d’une propriété, ainsi que [ReadOnly](../modifiers/readonly.md) ou [WriteOnly](../modifiers/writeonly.md).  
  
- **Inheritance.** Si l’interface utilise l' [instruction Inherits](inherits-statement.md), vous pouvez spécifier une ou plusieurs interfaces de base. Vous pouvez hériter de deux interfaces, même si elles définissent un membre portant le même nom. Dans ce cas, le code d’implémentation doit utiliser la qualification de nom pour spécifier le membre qu’il implémente.  
  
     Une interface ne peut pas hériter d’une autre interface avec un niveau d’accès plus restrictif. Par exemple, une `Public` interface ne peut pas hériter d’une `Friend` interface.  
  
     Une interface ne peut pas hériter d’une interface imbriquée dans celle-ci.  
  
- **Déploiement.** Quand une classe utilise l’instruction [Implements](implements-clause.md) pour implémenter cette interface, elle doit implémenter chaque membre défini dans l’interface. En outre, chaque signature dans le code d’implémentation doit correspondre exactement à la signature correspondante définie dans cette interface. Toutefois, le nom du membre dans le code d’implémentation ne doit pas nécessairement correspondre au nom de membre défini dans l’interface.  
  
     Quand une classe implémente une procédure, elle ne peut pas désigner la procédure comme `Shared` .  
  
- **Propriété par défaut.** Une interface peut spécifier au plus une propriété comme *propriété par défaut*, qui peut être référencée sans utiliser le nom de la propriété. Vous spécifiez une telle propriété en la déclarant avec le modificateur [par défaut](../modifiers/default.md) .  
  
     Notez que cela signifie qu’une interface peut définir une propriété par défaut uniquement si elle hérite de la valeur None.  
  
## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Tous les membres d’interface ont implicitement un accès [public](../modifiers/public.md) . Vous ne pouvez pas utiliser de modificateur d’accès lors de la définition d’un membre. Toutefois, une classe qui implémente l’interface peut déclarer un niveau d’accès pour chaque membre implémenté.  
  
     Si vous assignez une instance de classe à une variable, le niveau d’accès de ses membres peut varier selon que le type de données de la variable est l’interface sous-jacente ou la classe d’implémentation. L'exemple suivant illustre ce comportement.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Si vous accédez aux membres de classe via `varAsInterface` , ils ont tous un accès public. Toutefois, si vous accédez aux membres par `varAsClass` le biais de, la `Sub` procédure a un `doSomething` accès privé.  
  
- **Étendue.** Une interface est dans la portée de l’espace de noms, de la classe, de la structure ou du module.  
  
     La portée de chaque membre d’interface est l’interface entière.  
  
- **Cycle.** Une interface n’a pas elle-même une durée de vie, ni ses membres. Lorsqu’une classe implémente une interface et qu’un objet est créé en tant qu’instance de cette classe, l’objet a une durée de vie au sein de l’application dans laquelle il s’exécute. Pour plus d’informations, consultez « Lifetime » dans l' [instruction de classe](class-statement.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `Interface` instruction pour définir une interface nommée `thisInterface` , qui doit être implémentée avec une `Property` instruction et une `Function` instruction.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Notez que les `Property` `Function` instructions et n’introduisent pas de blocs se terminant par `End Property` et `End Function` dans l’interface. L’interface définit uniquement les signatures de ses membres. Les `Property` blocs complets et `Function` apparaissent dans une classe qui implémente `thisInterface` .  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
- [Class (instruction)](class-statement.md)
- [Module, instruction](module-statement.md)
- [Structure, instruction](structure-statement.md)
- [Property Statement](property-statement.md)
- [Function (instruction)](function-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Dans](../modifiers/in-generic-modifier.md)
- [Sortie](../modifiers/out-generic-modifier.md)
