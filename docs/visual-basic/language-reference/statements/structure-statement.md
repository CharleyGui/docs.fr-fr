---
title: Structure, instruction (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: ac128e257269ca301400bd8b294539d1ec836cab
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038620"
---
# <a name="structure-statement"></a>Structure, instruction

Déclare le nom d’une structure et introduit la définition des variables, propriétés, événements et procédures que la structure comprend.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
    [ Implements interfacenames ]
    [ datamemberdeclarations ]
    [ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>Composants

|Terme|Définition|
|---|---|
|`attributelist`|Optionnel. Consultez la [liste des attributs](attribute-list.md).|
|`accessmodifier`|Optionnel. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [public](../modifiers/public.md)<br />-   [protégé](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [privé](../modifiers/private.md)<br />- [Protected Friend](../modifiers/protected-friend.md)<br/>[protégé -  privé](../modifiers/private-protected.md) <br /><br /> Consultez [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Optionnel. Consultez [Shadows](../modifiers/shadows.md).|
|`Partial`|Optionnel. Indique une définition partielle de la structure. Voir [Partial](../modifiers/partial.md).|
|`name`|Requis. Nom de cette structure. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|Optionnel. Spécifie qu’il s’agit d’une structure générique.|
|`typelist`|Obligatoire si vous utilisez le mot clé [of](of-clause.md) . Liste des paramètres de type pour cette structure. Consultez la [liste des types](type-list.md).|
|`Implements`|Optionnel. Indique que cette structure implémente les membres d’une ou de plusieurs interfaces. Consultez [Implements, instruction](implements-statement.md).|
|`interfacenames`|Obligatoire si vous utilisez l’instruction `Implements`. Noms des interfaces implémentées par cette structure.|
|`datamemberdeclarations`|Requis. Zéro ou plusieurs instructions `Const`, `Dim`, `Enum` ou `Event` qui déclarent des *données membres* de la structure.|
|`methodmemberdeclarations`|Optionnel. Zéro, une ou plusieurs déclarations des procédures `Function`, `Operator`, `Property` ou `Sub`, qui servent de *membres de méthode* de la structure.|
|`End Structure`|Requis. Met fin à la définition de `Structure`.|

## <a name="remarks"></a>Notes

L’instruction `Structure` définit un type valeur composite que vous pouvez personnaliser. Une *structure* est une généralisation du type défini par l’utilisateur (UDT) des versions antérieures de Visual Basic. Pour plus d’informations, consultez [structures](../../programming-guide/language-features/data-types/structures.md).

Les structures prennent en charge un grand nombre des mêmes fonctionnalités que les classes. Par exemple, les structures peuvent avoir des propriétés et des procédures, elles peuvent implémenter des interfaces, et elles peuvent avoir des constructeurs paramétrables. Toutefois, il existe des différences significatives entre les structures et les classes dans des domaines tels que l’héritage, les déclarations et l’utilisation. En outre, les classes sont des types référence et les structures sont des types valeur. Pour plus d’informations, consultez [structures et classes](../../programming-guide/language-features/data-types/structures-and-classes.md).

Vous pouvez utiliser `Structure` uniquement au niveau de l’espace de noms ou du module. Cela signifie que le *contexte de déclaration* pour une structure doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Les structures ont par défaut un accès [Friend](../modifiers/friend.md) . Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Règles

- **Imbrication.** Vous pouvez définir une structure dans une autre. La structure externe est appelée *structure contenante*, et la structure interne est appelée *structure imbriquée*. Toutefois, vous ne pouvez pas accéder aux membres d’une structure imbriquée par le biais de la structure conteneur. Au lieu de cela, vous devez déclarer une variable du type de données de la structure imbriquée.

- **Déclaration de membre.** Vous devez déclarer chaque membre d’une structure. Un membre de structure ne peut pas être [protégé](../modifiers/protected.md) ou `Protected Friend`, car rien ne peut hériter d’une structure. Toutefois, la structure elle-même peut être `Protected` ou `Protected Friend`.
  
     Vous pouvez déclarer zéro ou plusieurs variables non partagées ou des événements non partagés non personnalisés dans une structure. Vous ne pouvez pas avoir uniquement des constantes, des propriétés et des procédures, même si certaines d’entre elles ne sont pas partagées.

- **D’initialisation.** Vous ne pouvez pas initialiser la valeur d’un membre de données non partagé d’une structure dans le cadre de sa déclaration. Vous devez soit initialiser ce membre de données au moyen d’un constructeur paramétrable sur la structure, soit assigner une valeur au membre après avoir créé une instance de la structure.

- **Héritage.** Une structure ne peut pas hériter d’un type autre que <xref:System.ValueType>, à partir duquel toutes les structures héritent. En particulier, une structure ne peut pas hériter d’une autre.

     Vous ne pouvez pas utiliser l' [instruction Inherits](inherits-statement.md) dans une définition de structure, même pour spécifier <xref:System.ValueType>.

- **Déploiement.** Si la structure utilise l' [instruction Implements](implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`.

- **Propriété par défaut.** Une structure peut spécifier au plus une propriété comme *propriété par défaut*, en utilisant le modificateur [default](../modifiers/default.md) . Pour plus d’informations, consultez [default](../modifiers/default.md).

## <a name="behavior"></a>Comportement

- **Niveau d’accès.** Dans une structure, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Tous les membres de la structure disposent par défaut d’un accès [public](../modifiers/public.md) . Notez que si la structure elle-même a un niveau d’accès plus restreint, cela restreint automatiquement l’accès à ses membres, même si vous ajustez leurs niveaux d’accès avec les modificateurs d’accès.

- **Étendue.** Une structure est dans la portée dans l’espace de noms, la classe, la structure ou le module qui le contient.

     La portée de chaque membre de la structure correspond à la structure entière.

- **Cycle.** Une structure n’a pas de durée de vie. Au lieu de cela, chaque instance de cette structure a une durée de vie indépendante de toutes les autres instances.

     La durée de vie d’une instance commence lorsqu’elle est créée par une [nouvelle clause Operator](../operators/new-operator.md) . Il se termine lorsque la durée de vie de la variable qui le contient se termine.

     Vous ne pouvez pas étendre la durée de vie d’une instance de structure. Une approximation de la fonctionnalité de structure statique est fournie par un module. Pour plus d’informations, consultez [module, instruction](module-statement.md).

     Les membres de structure ont des durées de vie en fonction de la façon et de l’emplacement de leur déclaration. Pour plus d’informations, consultez « Lifetime » dans l' [instruction de classe](class-statement.md).

- **Bénéfice.** Le code en dehors d’une structure doit qualifier le nom d’un membre avec le nom de cette structure.

     Si le code à l’intérieur d’une structure imbriquée crée une référence non qualifiée à un élément de programmation, Visual Basic recherche l’élément en premier dans la structure imbriquée, puis dans sa structure conteneur, et ainsi de suite jusqu’à l’élément conteneur le plus à l’extérieur. Pour plus d'informations, consultez [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Consommation de mémoire.** Comme avec tous les types de données composites, vous ne pouvez pas calculer en toute sécurité la consommation de mémoire totale d’une structure en additionnant les allocations de stockage nominal de ses membres. En outre, vous ne pouvez pas supposer sans risque que l’ordre de stockage en mémoire est le même que celui de votre ordre de déclaration. Si vous devez contrôler la disposition de stockage d’une structure, vous pouvez appliquer l’attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> à l’instruction `Structure`.

## <a name="example"></a>Exemple

L’exemple suivant utilise l’instruction `Structure` pour définir un ensemble de données associées pour un employé. Il illustre l’utilisation des membres `Public`, `Friend` et `Private` pour refléter la sensibilité des éléments de données. Il montre également les membres des procédures, des propriétés et des événements.

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

Pour plus d’informations sur l’utilisation de `Structure`s, consultez [variable de structure](../../programming-guide/language-features/data-types/structure-variables.md).

## <a name="see-also"></a>Voir aussi

- [Class (instruction)](class-statement.md)
- [Interface (instruction)](interface-statement.md)
- [Module (instruction)](module-statement.md)
- [Dim (instruction)](dim-statement.md)
- [Const (instruction)](const-statement.md)
- [Enum (instruction)](enum-statement.md)
- [Event (instruction)](event-statement.md)
- [Operator (instruction)](operator-statement.md)
- [Property (instruction)](property-statement.md)
- [Structures et classes](../../programming-guide/language-features/data-types/structures-and-classes.md)
