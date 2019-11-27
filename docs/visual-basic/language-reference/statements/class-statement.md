---
title: Class, instruction
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 3cb276f134e90ce3b3009234eb980d89477e0d09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354146"
---
# <a name="class-statement-visual-basic"></a>Class, instruction (Visual Basic)
Déclare le nom d’une classe et introduit la définition des variables, propriétés, événements et procédures que la classe comprend.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attributelist`|Ce paramètre est facultatif. Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Ce paramètre est facultatif. Il peut s'agir de l'un des éléments suivants :<br /><br /> -   [public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />[protégé - privé](../../language-reference/modifiers/private-protected.md)<br/><br/> Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Ce paramètre est facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Ce paramètre est facultatif. Consultez [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Ce paramètre est facultatif. Voir [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Ce paramètre est facultatif. Indique une définition partielle de la classe. Voir [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Requis. Nom de cette classe. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Ce paramètre est facultatif. Spécifie qu’il s’agit d’une classe générique.|  
|`typelist`|Obligatoire si vous utilisez le mot clé [of](../../../visual-basic/language-reference/statements/of-clause.md) . Liste des paramètres de type pour cette classe. Consultez la [liste des types](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Ce paramètre est facultatif. Indique que cette classe hérite des membres d’une autre classe. Consultez [Inherits (instruction](../../../visual-basic/language-reference/statements/inherits-statement.md)).|  
|`classname`|Obligatoire si vous utilisez l’instruction `Inherits`. Nom de la classe dont cette classe est dérivée.|  
|`Implements`|Ce paramètre est facultatif. Indique que cette classe implémente les membres d’une ou de plusieurs interfaces. Consultez [Implements, instruction](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Obligatoire si vous utilisez l’instruction `Implements`. Noms des interfaces implémentées par cette classe.|  
|`statements`|Ce paramètre est facultatif. Les instructions qui définissent les membres de cette classe.|  
|`End Class`|Requis. Met fin à la définition de `Class`.|  
  
## <a name="remarks"></a>Notes  
 Une instruction `Class` définit un nouveau type de données. Une *classe* est un bloc de construction fondamental de la programmation orientée objet (OOP). Pour plus d’informations, consultez [objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Vous pouvez utiliser `Class` uniquement au niveau de l’espace de noms ou du module. Cela signifie que le *contexte de déclaration* pour une classe doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Chaque instance d’une classe a une durée de vie indépendante de toutes les autres instances. Cette durée de vie commence lorsqu’elle est créée par une nouvelle clause d' [opérateur](../../../visual-basic/language-reference/operators/new-operator.md) ou par une fonction comme <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Il se termine lorsque toutes les variables qui pointent vers l’instance ont été définies sur [Nothing](../../../visual-basic/language-reference/nothing.md) ou sur des instances d’autres classes.  
  
 Les classes ont par défaut un accès [Friend](../../../visual-basic/language-reference/modifiers/friend.md) . Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
- **Imbrication.** Vous pouvez définir une classe dans une autre. La classe externe est appelée *classe conteneur*et la classe interne est appelée *classe imbriquée*.  
  
- **Héritage.** Si la classe utilise l' [instruction Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), vous ne pouvez spécifier qu’une seule classe de base ou interface. Une classe ne peut pas hériter de plusieurs éléments.  
  
     Une classe ne peut pas hériter d’une autre classe avec un niveau d’accès plus restrictif. Par exemple, une classe `Public` ne peut pas hériter d’une classe `Friend`.  
  
     Une classe ne peut pas hériter d’une classe imbriquée dans celle-ci.  
  
- **Déploiement.** Si la classe utilise l' [instruction Implements](../../../visual-basic/language-reference/statements/implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`. Une exception est la réimplémentation d’un membre de classe de base. Pour plus d’informations, consultez « reimplementation » dans [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Propriété par défaut.** Une classe peut spécifier au plus une propriété comme *propriété par défaut*. Pour plus d’informations, consultez [default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Dans une classe, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Les membres de classe disposent par défaut d’un accès [public](../../../visual-basic/language-reference/modifiers/public.md) , à l’exception des variables et des constantes, qui ont par défaut un accès [privé](../../../visual-basic/language-reference/modifiers/private.md) . Quand une classe a un accès plus restreint que l’un de ses membres, le niveau d’accès à la classe est prioritaire.  
  
- **Étendue.** Une classe est dans la portée dans l’espace de noms, la classe, la structure ou le module qui le contient.  
  
     La portée de chaque membre de classe correspond à la classe entière.  
  
     **Cycle.** Visual Basic ne prend pas en charge les classes statiques. L’équivalent fonctionnel d’une classe statique est fourni par un module. Pour plus d’informations, consultez [module, instruction](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Les membres de classe ont des durées de vie selon le mode et l’emplacement de leur déclaration. Pour plus d’informations, consultez [durée de vie dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Bénéfice.** Le code en dehors d’une classe doit qualifier le nom d’un membre avec le nom de cette classe.  
  
     Si du code à l’intérieur d’une classe imbriquée crée une référence non qualifiée à un élément de programmation, Visual Basic recherche l’élément en premier dans la classe imbriquée, puis dans sa classe conteneur, et ainsi de suite jusqu’à l’élément conteneur le plus à l’extérieur.  
  
## <a name="classes-and-modules"></a>Classes et modules  
 Ces éléments présentent de nombreuses similitudes, mais il existe également des différences importantes.  
  
- **Correspondance.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : les *modules de classe* (fichiers. CLS) et les *modules standard* (fichiers. bas). La version actuelle appelle ces *classes* et ces *modules*, respectivement.  
  
- **Membres partagés.** Vous pouvez contrôler si un membre d’une classe est un membre d’instance ou partagé.  
  
- **Orientation de l’objet.** Les classes sont orientées objet, mais les modules ne le sont pas. Vous pouvez créer une ou plusieurs instances d’une classe. Pour plus d’informations, consultez [objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une instruction `Class` pour définir une classe et plusieurs membres.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Voir aussi

- [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Structures et classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Durée de vie d’un objet : création et destruction des objets](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
