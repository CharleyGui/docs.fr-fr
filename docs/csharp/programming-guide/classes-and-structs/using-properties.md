---
title: Utilisation de propriétés - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452017"
---
# <a name="using-properties-c-programming-guide"></a>Utilisation de propriétés (Guide de programmation C#)

Les propriétés allient des caractéristiques des champs et des méthodes. Pour l’utilisateur d’un objet, une propriété s’apparente à un champ. Pour accéder à celle-ci, il doit utiliser la même syntaxe. Pour l’implémenteur d’une classe, une propriété est constituée d’un ou deux blocs de code, représentant un accesseur [get](../../language-reference/keywords/get.md) et/ou un accesseur [set](../../language-reference/keywords/set.md). Le bloc de code correspondant à l’accesseur `get` est exécuté à la lecture de la propriété ; le bloc de code correspondant à l’accesseur `set` est exécuté au moment où une nouvelle valeur est assignée à la propriété. Une propriété sans accesseur `set` est considérée comme étant en lecture seule. Une propriété sans accesseur `get` est considérée comme étant en écriture seule. Une propriété qui possède les deux accesseurs est en lecture-écriture.

Contrairement aux champs, les propriétés ne sont pas classifiées en tant que variables. Par conséquent, vous ne pouvez pas passer une propriété en tant que paramètre [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).

Les propriétés ont diverses utilisations : elles peuvent valider les données avant d’autoriser une modification ; elles peuvent exposer de manière transparente les données d’une classe quand celles-ci sont effectivement extraites d’une autre source, telle qu’une base de données ; elles peuvent effectuer une action quand des données sont modifiées, comme déclencher un événement ou modifier la valeur d’autres champs.

Les propriétés sont déclarées dans le bloc de classe en spécifiant le niveau d’accès du champ, suivi du type de la propriété, du nom de la propriété et d’un bloc de code qui déclare un accesseur `get` et/ou un accesseur `set`. Par exemple :

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

Dans cet exemple, `Month` est déclaré en tant que propriété pour permettre à l’accesseur `set` de vérifier que la valeur définie de `Month` se trouve bien entre 1 et 12. La propriété `Month` utilise un champ privé pour assurer le suivi de la valeur réelle. L’emplacement réel des données d’une propriété est souvent appelé « magasin de stockage » de la propriété. Il est courant que les propriétés utilisent des champs privés comme magasin de stockage. Le champ est marqué comme étant privé pour garantir qu’il ne peut être modifié qu’en appelant la propriété. Pour plus d’informations sur les restrictions d’accès public et privé, consultez [Modificateurs d’accès](./access-modifiers.md).

Les propriétés implémentées automatiquement fournissent une syntaxe simplifiée pour des déclarations de propriété simples. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](auto-implemented-properties.md).

## <a name="the-get-accessor"></a>Accesseur get

Le corps de l’accesseur `get` ressemble à celui d’une méthode. Il doit retourner une valeur du type de la propriété. L’exécution de l’accesseur `get` revient à lire la valeur du champ. Par exemple, quand vous retournez la variable privée de l’accesseur `get` et que les optimisations sont activées, l’appel à la méthode de l’accesseur `get` est intégré (inline) par le compilateur, si bien il n’existe aucune surcharge d’appel de méthode. Cependant, une méthode d’accesseur `get` virtuelle ne peut pas être inline, car le compilateur ne sait pas au moment de la compilation quelle méthode peut être effectivement appelée au moment de l’exécution. Voici un exemple d’accesseur `get` qui retourne la valeur d’un champ privé `_name` :

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Quand vous faites référence à la propriété (pas en tant que cible d’une assignation), l’accesseur `get` est appelé pour lire la valeur de la propriété. Par exemple :

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

L’accesseur `get` doit se terminer dans une instruction [return](../../language-reference/keywords/return.md) ou [throw](../../language-reference/keywords/throw.md) et le contrôle ne peut pas déborder du corps de l’accesseur.

Modifier l’état de l’objet en utilisant l’accesseur `get` n’est pas un style de programmation approprié. Par exemple, l’accesseur suivant s’accompagne d’un effet secondaire, à savoir que l’état de l’objet est modifié chaque fois que le champ `_number` fait l’objet d’un accès.

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

L’accesseur `get` peut être utilisé pour retourner la valeur du champ ou pour la calculer et la retourner. Par exemple :

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

Dans le segment de code précédent, si vous n’assignez pas de valeur à la propriété `Name`, elle retourne la valeur `NA`.

## <a name="the-set-accessor"></a>Accesseur Set

L’accesseur `set` ressemble à une méthode dont le type de retour est [void](../../language-reference/builtin-types/void.md). Il utilise un paramètre implicite nommé `value`, dont le type est celui de la propriété. Dans l’exemple ci-dessous, un accesseur `set` est ajouté à la propriété `Name` :

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Quand vous assignez une valeur à la propriété, l’accesseur `set` est appelé en utilisant un argument qui fournit la nouvelle valeur. Par exemple :

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

Il s’agit d’une erreur d’utiliser le nom de paramètre implicite, `value`, pour une déclaration de variable locale dans un accesseur `set`.

## <a name="remarks"></a>Notes

Les propriétés peuvent être marquées comme étant `public`, `private`, `protected`, `internal`, `protected internal` ou `private protected`. Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder à la propriété. Les accesseurs `get` et `set` d’une même propriété peuvent avoir des modificateurs d’accès différents. Par exemple, l’accesseur `get` peut être `public` pour autoriser l’accès en lecture seule en dehors du type, tandis que l’accesseur `set` peut être `private` ou `protected`. Pour plus d’informations, consultez la page [Modificateurs d’accès](./access-modifiers.md).

Une propriété peut être déclarée en tant que propriété statique à l’aide du mot clé `static`. La propriété devient ainsi accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](./static-classes-and-static-class-members.md).

Une propriété peut être marquée comme étant une propriété virtuelle à l’aide du mot clé [virtual](../../language-reference/keywords/virtual.md). Cela permet aux classes dérivées de substituer le comportement de la propriété à l’aide du mot clé [override](../../language-reference/keywords/override.md). Pour plus d'informations sur ces options, consultez [Héritage](inheritance.md).

Un propriété qui se substitue à une propriété virtuelle peut aussi être [sealed](../../language-reference/keywords/sealed.md), ce qui signifie que pour les classes dérivées, elle n’est plus virtuelle. Enfin, une propriété peut être déclarée comme étant [abstract](../../language-reference/keywords/abstract.md). Cela signifie qu’il n’existe aucune implémentation dans la classe et que les classes dérivées doivent écrire leur propre implémentation. Pour plus d’informations sur ces options, consultez [Classes abstract et sealed et membres de classe](abstract-and-sealed-classes-and-class-members.md).
  
> [!NOTE]
> Il s’agit d’une erreur d’utiliser un modificateur [virtual](../../language-reference/keywords/virtual.md), [abstract](../../language-reference/keywords/abstract.md) ou [override](../../language-reference/keywords/override.md) sur un accesseur de propriété [static](../../language-reference/keywords/static.md).

## <a name="example"></a>Exemple

Cet exemple illustre les propriétés d’instance, statiques et en lecture seule. Il accepte le nom de l’employé à partir du clavier, incrémente `NumberOfEmployees` de 1 et affiche le nom et le numéro de l’employé.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Exemple

Cet exemple montre comment accéder à une propriété d’une classe de base qui est masquée par une autre propriété qui porte le même nom dans une classe dérivée :

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Voici les points importants de l’exemple précédent :

- La propriété `Name` de la classe dérivée masque la propriété `Name` de la classe de base. En pareil cas, le modificateur `new` est utilisé dans la déclaration de la propriété de la classe dérivée :

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- La conversion de type `(Employee)` est utilisée pour accéder à la propriété masquée de la classe de base :

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Pour plus d’informations sur le masquage des membres, consultez [new, modificateur](../../language-reference/keywords/new-modifier.md).

## <a name="example"></a>Exemple

Dans cet exemple, deux classes, `Cube` et `Square`, implémentent une classe abstract, `Shape`, et remplacent sa propriété `Area` abstract. Notez l’utilisation du modificateur [override](../../language-reference/keywords/override.md) sur les propriétés. Le programme accepte le côté (« side ») comme entrée et calcule les surfaces (« areas ») du carré (« square ») et du cube. De même, il accepte la surface (« area ») comme entrée et calcule le côté (« side ») correspondant du carré (« square ») et du cube.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Propriétés](properties.md)
- [Propriété d’une interface](interface-properties.md)
- [Propriétés implémentées automatiquement](auto-implemented-properties.md)
