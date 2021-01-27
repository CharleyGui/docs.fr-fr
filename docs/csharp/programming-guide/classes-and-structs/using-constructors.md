---
title: Utilisation de constructeurs - Guide de programmation C#
description: Cet exemple montre comment une classe est instanciée à l’aide de l’opérateur New en C#. Le constructeur simple est appelé après que la mémoire a été allouée pour le nouvel objet.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 161c243f16f6705fa8fcf79360f92a74e4d0b27b
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899254"
---
# <a name="using-constructors-c-programming-guide"></a>Utilisation de constructeurs (Guide de programmation C#)

Quand une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md) est créé, son constructeur est appelé. Les constructeurs portent le même nom que la classe ou le struct, et ils initialisent généralement les membres de données du nouvel objet.  
  
 Dans l’exemple suivant, une classe nommée `Taxi` est définie en utilisant un constructeur simple. Cette classe est ensuite instanciée à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md). Le constructeur `Taxi` est appelé par l’opérateur `new` immédiatement après l’allocation de la mémoire pour le nouvel objet.  
  
 [!code-csharp[TaxiExample#1](snippets/using-constructors/Program.cs#1)]
  
 Un constructeur qui ne prend pas de paramètres est appelé *constructeur sans paramètre*. Les constructeurs sans paramètre sont appelés chaque fois qu’un objet est instancié à l’aide de l’opérateur `new` et qu’aucun argument n’est fourni à `new`. Pour plus d’informations, consultez [Constructeurs d’instances](./instance-constructors.md).  
  
 À moins d’être [statiques](../../language-reference/keywords/static.md), les classes sans constructeur se voient attribuer un constructeur public sans paramètre par le compilateur C#, afin d’activer l’instanciation de classe. Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](./static-classes-and-static-class-members.md).  
  
 Vous pouvez empêcher qu’une classe soit instanciée en rendant le constructeur privé, comme suit :  
  
 [!code-csharp[PrivateConstructor#2](snippets/using-constructors/Program.cs#2)]
  
 Pour plus d’informations, consultez [Constructeurs privés](./private-constructors.md).  
  
 Les constructeurs des types [struct](../../language-reference/builtin-types/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur explicite sans paramètre, car le compilateur en fournit automatiquement un. Ce constructeur initialise chaque champ du `struct` à la [valeur par défaut](../../language-reference/builtin-types/default-values.md). Toutefois, ce constructeur sans paramètre est appelé uniquement si le `struct` est instancié avec `new`. Par exemple, ce code utilise le constructeur sans paramètre pour <xref:System.Int32>. Vous avez ainsi la garantie que l’entier est initialisé :  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Toutefois, le code suivant provoque une erreur de compilateur, car il n’utilise pas `new` et il essaie d’utiliser un objet qui n’a pas été initialisé :  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Les objets basés sur des `structs` (notamment tous les types numériques intégrés) peuvent également être initialisés ou assignés, puis utilisés, comme dans l’exemple suivant :  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 L’appel du constructeur sans paramètre pour un type valeur n’est donc pas obligatoire.  
  
 Les classes et les `structs` peuvent tous les deux définir des constructeurs qui prennent des paramètres. Les constructeurs qui prennent des paramètres doivent être appelés à l’aide d’une instruction `new` ou d’une instruction [base](../../language-reference/keywords/base.md). Les classes et les `structs` peuvent également définir plusieurs constructeurs, et ni les classes ni les structs ne sont nécessaires pour définir un constructeur sans paramètre. Par exemple :  
  
 [!code-csharp[EmployeeExample#3](snippets/using-constructors/Program.cs#3)]
  
 Cette classe peut être créée à l’aide de l’une ou l’autre des instructions suivantes :  
  
 [!code-csharp[InstantiatingEmployeeConstructors#4](snippets/using-constructors/Program.cs#4)]
  
 Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d’une classe de base. Par exemple :  
  
 [!code-csharp[ManagerInheritingEmployee#5](snippets/using-constructors/Program.cs#5)]
  
 Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur ne soit exécuté. Le mot clé `base` peut être utilisé avec ou sans paramètres. Tous les paramètres du constructeur peuvent être utilisés comme paramètres pour `base` ou comme partie d’une expression. Pour plus d’informations, consultez [base](../../language-reference/keywords/base.md).  
  
 Dans une classe dérivée, si un constructeur de classe de base n’est pas appelé explicitement à l’aide du mot clé `base`, le constructeur sans paramètre, s’il existe, est appelé implicitement. Cela signifie que les déclarations de constructeur suivantes sont en fait les mêmes :  
  
 [!code-csharp[ManagerImplicitlyCallingParameterlessBaseConstructor#6](snippets/using-constructors/Program.cs#6)]
  
 [!code-csharp[ManagerExplicitlyCallingParameterlessBaseConstructor#7](snippets/using-constructors/Program.cs#7)]
  
 Si une classe de base n’offre pas de constructeur sans paramètre, la classe dérivée doit faire un appel explicite à un constructeur de base à l’aide de `base`.  
  
 Un constructeur peut appeler un autre constructeur dans le même objet à l’aide du mot clé [this](../../language-reference/keywords/this.md). Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles comme paramètres pour `this` ou comme partie d’une expression. Par exemple, le deuxième constructeur de l’exemple précédent peut être récrit à l’aide de `this` :  
  
 [!code-csharp[EmployeeCallingConstructorInSameClass#8](snippets/using-constructors/Program.cs#8)]
  
 L’utilisation du mot clé `this` dans l’exemple précédent provoque l’appel de ce constructeur :  
  
 [!code-csharp[ConstructorBeingCalledByThisKeyword#9](snippets/using-constructors/Program.cs#9)]
  
 Les constructeurs peuvent être marqués comme [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) ou [private protected](../../language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent construire la classe. Pour plus d’informations, consultez [Modificateurs d’accès](./access-modifiers.md).  
  
 Un constructeur peut être déclaré statique à l’aide du mot clé [static](../../language-reference/keywords/static.md). Les constructeurs statiques sont appelés automatiquement, juste avant que des champs statiques soient accessibles, et ils sont généralement utilisés pour initialiser des membres de classe statique. Pour plus d’informations, consultez [Constructeurs statiques](./static-constructors.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Constructeurs d’instances](~/_csharplang/spec/classes.md#instance-constructors) et [Constructeurs statiques](~/_csharplang/spec/classes.md#static-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Finaliseurs](./destructors.md)
