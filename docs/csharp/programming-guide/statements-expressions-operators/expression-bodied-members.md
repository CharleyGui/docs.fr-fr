---
title: Membres expression-bodied - Guide de programmation C#
description: En savoir plus sur les membres expression-extracorporels. Consultez des exemples de code qui utilisent la définition de corps d’expression pour les propriétés, les constructeurs, les finaliseurs et bien plus encore.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381656"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Membres expression-bodied (Guide de programmation C#)

Les définitions de corps d’expression vous permettent de fournir l’implémentation d’un membre sous une forme lisible et très concise. Vous pouvez utiliser une définition de corps d’expression chaque fois que la logique d’un membre pris en charge, comme une méthode ou une propriété, se compose d’une seule expression. La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où *expression* est une expression valide.

La prise en charge des définitions de corps d’expression a été introduite pour les méthodes et les propriétés en lecture seule dans C# 6 et a été étendue dans C# 7.0. Vous pouvez utiliser des définitions de corps d’expression avec les membres de type listés dans le tableau suivant :

|Membre  |Prise en charge à compter de |
|---------|---------|
|[Méthode](#methods)  |C# 6 |
|[Propriété en lecture seule](#read-only-properties)   |C# 6  |
|[Propriété](#properties)  |C# 7.0 |
|[Constructeur](#constructors)   |C# 7.0 |
|[Finaliseur](#finalizers)     |C# 7.0 |
|[Indexeur](#indexers)       |C# 7.0 |

## <a name="methods"></a>Méthodes

Une méthode expression-bodied se compose d’une seule expression qui retourne une valeur dont le type correspond au type de retour de la méthode ou, pour les méthodes qui retournent `void`, qui effectue une opération. Par exemple, les types qui substituent la méthode <xref:System.Object.ToString%2A> incluent généralement une expression unique qui retourne la représentation sous forme de chaîne de l’objet actuel.

L’exemple suivant définit une classe `Person` qui substitue la méthode <xref:System.Object.ToString%2A> avec une définition de corps d’expression. Il définit également une méthode `DisplayName` qui affiche un nom sur la console. Notez que le mot clé `return` n’est pas utilisé dans la définition de corps d’expression `ToString`.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Pour plus d’informations, consultez [Méthodes (Guide de programmation C#)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Propriétés en lecture seule

Depuis C# 6, vous pouvez utiliser une définition de corps d’expression pour implémenter une propriété en lecture seule. Pour ce faire, utilisez la syntaxe suivante :

```csharp
PropertyType PropertyName => expression;
```

L’exemple suivant définit une classe `Location` dont la propriété en lecture seule `Name` est implémentée comme une définition de corps d’expression qui retourne la valeur du champ privé `locationName` :

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Pour plus d’informations sur les propriétés, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).

## <a name="properties"></a>Propriétés

Depuis C# 7.0, vous pouvez utiliser des définitions de corps d’expression pour implémenter la propriété `get` et les accesseurs `set`. L’exemple suivant montre comment faire :

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Pour plus d’informations sur les propriétés, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Constructeurs

Une définition de corps d’expression pour un constructeur se compose généralement d’une seule expression d’assignation ou d’un appel de méthode qui gère les arguments du constructeur ou qui initialise l’état de l’instance.

L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*. La définition de corps d’expression assigne l’argument à la propriété `Name`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Pour plus d’informations, consultez [Constructeurs (Guide de programmation C#)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finaliseurs

Une définition de corps d’expression pour un finaliseur contient généralement des instructions de nettoyage, telles que des instructions qui libèrent les ressources non managées.

L’exemple suivant définit un finaliseur qui utilise une définition de corps d’expression pour indiquer que le finaliseur a été appelé.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Pour plus d’informations, consultez [Finaliseurs (Guide de programmation C#)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexeurs

Comme avec les propriétés, l’indexeur `get` et les `set` accesseurs se composent de définitions de corps d’expression si l' `get` accesseur se compose d’une expression unique qui retourne une valeur ou l' `set` accesseur effectue une assignation simple.

L’exemple suivant définit une classe nommée `Sports` qui inclut un tableau <xref:System.String> interne contenant les noms de plusieurs sports. L’indexeur `get` et les `set` accesseurs sont tous deux implémentés en tant que définitions de corps d’expression.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Pour plus d’informations, consultez [Indexeurs (Guide de programmation C#)](../indexers/index.md).
