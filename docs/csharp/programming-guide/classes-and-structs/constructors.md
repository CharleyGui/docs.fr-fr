---
title: Constructeurs - Guide de programmation C#
description: Un constructeur en C# est appelé lors de la création d’une classe ou d’un struct. Utilisez les constructeurs pour définir les valeurs par défaut, l’instanciation de limite et écrire du code flexible et facile à lire.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: e8758d7322d7fde45ccbd9eaf9248a3168980bd3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555339"
---
# <a name="constructors-c-programming-guide"></a>Constructeurs (guide de programmation C#)

Chaque fois qu’une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md) est créé, son constructeur est appelé. Une classe ou un struct peut avoir plusieurs constructeurs qui prennent des arguments différents. Les constructeurs permettent au programmeur de définir des valeurs par défaut, de limiter l’instanciation et d’écrire un code flexible et facile à lire. Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de constructeurs](./using-constructors.md) et [Constructeurs d’instances](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Constructeurs sans paramètre
  
Si vous ne fournissez pas de constructeur pour votre classe, C# en crée un par défaut qui instancie l’objet et définit des variables membres avec les valeurs par défaut, comme indiqué dans l’article [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md) . Si vous ne fournissez pas de constructeur pour votre struct, C# s’appuie sur un *constructeur sans paramètre implicite* pour initialiser automatiquement chaque champ à sa valeur par défaut. Pour plus d’informations et d’exemples, consultez [constructeurs d’instances](instance-constructors.md).  

## <a name="constructor-syntax"></a>Syntaxe du constructeur

Un constructeur est une méthode dont le nom est le même que celui de son type. Sa signature de méthode inclut uniquement le nom de la méthode et sa liste de paramètres ; elle n’inclut pas de type de retour. L’exemple suivant affiche le constructeur d’une classe nommée `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Si un constructeur peut être implémenté comme une seule instruction, vous pouvez utiliser une [définition de corps d’expression](../statements-expressions-operators/expression-bodied-members.md). L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*. La définition de corps d’expression assigne l’argument au champ `locationName`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Constructeurs statiques

Les exemples précédents ont tous montré des constructeurs d’instances qui permettent de créer un objet. Une classe ou un struct peut également avoir un constructeur statique qui initialise les membres statiques du type.  Les constructeurs statiques sont sans paramètre. Si vous ne fournissez pas de constructeur statique pour initialiser les champs statiques, le compilateur C# initialise les champs statiques à leur valeur par défaut, comme indiqué dans l’article [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md) .

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
  
 [Comment : écrire un constructeur de copie](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Finaliseurs](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Pourquoi les initialiseurs s’exécutent-ils dans l’ordre inverse en tant que constructeurs ? Première partie](/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
