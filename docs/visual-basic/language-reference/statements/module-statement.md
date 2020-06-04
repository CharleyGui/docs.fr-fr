---
title: Module, instruction
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404450"
---
# <a name="module-statement"></a>Module, instruction

Déclare le nom d’un module et introduit la définition des variables, propriétés, événements et procédures que le module comprend.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>Éléments

`attributelist`  
Facultatif. Consultez la [liste des attributs](attribute-list.md).

`accessmodifier`  
Facultatif. Il peut s'agir d'une des méthodes suivantes :

- [Public](../modifiers/public.md)

- [Contact](../modifiers/friend.md)

Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

`name`  
Obligatoire. Nom de ce module. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).

`statements`  
Facultatif. Les instructions qui définissent les variables, les propriétés, les événements, les procédures et les types imbriqués de ce module.

`End Module`  
Met fin à la `Module` définition.

## <a name="remarks"></a>Notes

Une `Module` instruction définit un type de référence disponible dans l’ensemble de son espace de noms. Un *module* (parfois appelé *module standard*) est semblable à une classe, mais avec des distinctions importantes. Chaque module a exactement une instance et n’a pas besoin d’être créé ou affecté à une variable. Les modules ne prennent pas en charge l’héritage ou implémentent des interfaces. Notez qu’un module n’est pas un *type* dans le sens où une classe ou une structure est : vous ne pouvez pas déclarer un élément de programmation pour avoir le type de données d’un module.

Vous pouvez utiliser `Module` uniquement au niveau de l’espace de noms. Cela signifie que le *contexte de déclaration* d’un module doit être un fichier source ou un espace de noms, et ne peut pas être une classe, une structure, un module, une interface, une procédure ou un bloc. Vous ne pouvez pas imbriquer un module dans un autre module ou dans n’importe quel type. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

Un module a la même durée de vie que votre programme. Étant donné que ses membres sont tous `Shared` , ils ont également une durée de vie égale à celle du programme.

Les modules ont par défaut un accès [Friend](../modifiers/friend.md) . Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Tous les membres d’un module sont implicitement `Shared` .

## <a name="classes-and-modules"></a>Classes et modules

Ces éléments présentent de nombreuses similitudes, mais il existe également des différences importantes.

- **Correspondance.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : les *modules de classe* (fichiers. CLS) et les *modules standard* (fichiers. bas). La version actuelle appelle ces *classes* et ces *modules*, respectivement.

- **Membres partagés.** Vous pouvez contrôler si un membre d’une classe est un membre d’instance ou partagé.

- **Orientation de l’objet.** Les classes sont orientées objet, mais les modules ne le sont pas. Ainsi, seules les classes peuvent être instanciées en tant qu’objets. Pour plus d’informations, consultez [objets et classes](../../programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Règles

- **Modificateurs.** Tous les membres de module sont implicitement [partagés](../modifiers/shared.md). Vous ne pouvez pas utiliser le `Shared` mot clé lors de la déclaration d’un membre et vous ne pouvez pas modifier l’état partagé d’un membre.

- **Inheritance.** Un module ne peut pas hériter d’un type autre que <xref:System.Object> , à partir duquel tous les modules héritent. En particulier, un module ne peut pas hériter d’un autre.

  Vous ne pouvez pas utiliser l' [instruction Inherits](inherits-statement.md) dans une définition de module, même pour spécifier <xref:System.Object> .

- **Propriété par défaut.** Vous ne pouvez pas définir de propriétés par défaut dans un module. Pour plus d’informations, consultez [default](../modifiers/default.md).

## <a name="behavior"></a>Comportement

- **Niveau d’accès.** Dans un module, vous pouvez déclarer chaque membre avec son propre niveau d’accès. Les membres du module disposent par défaut d’un accès [public](../modifiers/public.md) , à l’exception des variables et des constantes, qui ont par défaut un accès [privé](../modifiers/private.md) . Quand un module a un accès plus restreint que l’un de ses membres, le niveau d’accès du module spécifié est prioritaire.

- **Étendue.** Un module est dans la portée tout au long de son espace de noms.

  La portée de chaque membre de module est le module entier. Notez que tous les membres subissent la *promotion de type*, ce qui entraîne la promotion de leur étendue en espace de noms contenant le module. Pour plus d’informations, consultez [promotion de type](../../programming-guide/language-features/declared-elements/type-promotion.md).

- **Bénéfice.** Vous pouvez avoir plusieurs modules dans un projet et vous pouvez déclarer des membres portant le même nom dans deux ou plusieurs modules. Toutefois, vous devez qualifier toute référence à un tel membre avec le nom de module approprié si la référence est en dehors de ce module. Pour plus d'informations, consultez [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="example"></a>Exemple

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>Voir aussi

- [Class (instruction)](class-statement.md)
- [Namespace, instruction](namespace-statement.md)
- [Structure, instruction](structure-statement.md)
- [Interface (instruction)](interface-statement.md)
- [Property Statement](property-statement.md)
- [Promotion de type](../../programming-guide/language-features/declared-elements/type-promotion.md)
