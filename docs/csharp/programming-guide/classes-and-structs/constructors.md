---
title: Constructeurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 13597275460c075309b7457485a17655cf93f251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971095"
---
# <a name="constructors-c-programming-guide"></a>Constructeurs (guide de programmation C#)

Chaque fois qu’une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/keywords/struct.md) est créé, son constructeur est appelé. Une classe ou un struct peut avoir plusieurs constructeurs qui prennent des arguments différents. Les constructeurs permettent au programmeur de définir des valeurs par défaut, de limiter l’instanciation et d’écrire un code flexible et facile à lire. Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de constructeurs](./using-constructors.md) et [Constructeurs d’instances](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Constructeurs sans paramètre
  
Si vous ne fournissez pas de constructeur pour votre classe, C# en crée un par défaut qui instancie l’objet et affecte aux variables membres les valeurs par défaut listées dans le [Tableau des valeurs par défaut](../../language-reference/keywords/default-values-table.md). Si vous ne fournissez pas de constructeur pour votre struct, le langage C# s’appuie sur un *constructeur implicite sans paramètre* pour initialiser automatiquement chaque champ d’un type valeur vers sa valeur par défaut (voir [Tableau des valeurs par défaut](../../language-reference/keywords/default-values-table.md)). Pour obtenir plus d’informations et d’exemples, consultez [Constructeurs d’instances](./instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe du constructeur

Un constructeur est une méthode dont le nom est le même que celui de son type. Sa signature de méthode inclut uniquement le nom de la méthode et sa liste de paramètres ; elle n’inclut pas de type de retour. L’exemple suivant affiche le constructeur d’une classe nommée `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Si un constructeur peut être implémenté comme une seule instruction, vous pouvez utiliser une [définition de corps d’expression](../statements-expressions-operators/expression-bodied-members.md). L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*. La définition de corps d’expression assigne l’argument au champ `locationName`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Constructeurs statiques

Les exemples précédents ont tous montré des constructeurs d’instances qui permettent de créer un objet. Une classe ou un struct peut également avoir un constructeur statique qui initialise les membres statiques du type.  Les constructeurs statiques sont sans paramètre. Si vous ne fournissez pas de constructeur statique pour initialiser les champs statiques, le compilateur C# initialise tous les champs statiques vers leur valeur par défaut (voir [Tableau des valeurs par défaut](../../language-reference/keywords/default-values-table.md)).

L’exemple suivant utilise un constructeur statique pour initialiser un champ statique.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Vous pouvez également définir un constructeur statique avec une définition de corps d’expression, comme l’illustre l’exemple suivant. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Pour obtenir plus d’informations et d’exemples, consultez [Constructeurs statiques](./static-constructors.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation de constructeurs](./using-constructors.md)  
  
 [Constructeurs d’instances](./instance-constructors.md)  
  
 [Constructeurs privés](./private-constructors.md)  
  
 [Constructeurs statiques](./static-constructors.md)  
  
 [Comment écrire un constructeur de copie](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Finaliseurs](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Pourquoi les initialiseurs s’exécutent-ils dans l’ordre inverse en tant que constructeurs ? Première partie](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
