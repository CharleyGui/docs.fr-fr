---
title: Utilisation de constructeurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 018710f753df261fce28e2e1cae1272b36923a05
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363010"
---
# <a name="using-constructors-c-programming-guide"></a>Utilisation de constructeurs (Guide de programmation C#)

Quand une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé. Les constructeurs portent le même nom que la classe ou le struct, et ils initialisent généralement les membres de données du nouvel objet.  
  
 Dans l’exemple suivant, une classe nommée `Taxi` est définie en utilisant un constructeur simple. Cette classe est ensuite instanciée à l’aide de l’opérateur [new](../../../csharp/language-reference/operators/new-operator.md). Le constructeur `Taxi` est appelé par l’opérateur `new` immédiatement après l’allocation de la mémoire pour le nouvel objet.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Un constructeur qui ne prend pas de paramètres est appelé *constructeur sans paramètre*. Les constructeurs sans paramètre sont appelés chaque fois qu’un objet est instancié à l’aide de l’opérateur `new` et qu’aucun argument n’est fourni à `new`. Pour plus d’informations, consultez [Constructeurs d’instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 À moins d’être [statiques](../../../csharp/language-reference/keywords/static.md), les classes sans constructeur se voient attribuer un constructeur public sans paramètre par le compilateur C#, afin d’activer l’instanciation de classe. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Vous pouvez empêcher qu’une classe soit instanciée en rendant le constructeur privé, comme suit :  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Pour plus d’informations, consultez [Constructeurs privés](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Les constructeurs des types [struct](../../../csharp/language-reference/keywords/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur explicite sans paramètre, car le compilateur en fournit automatiquement un. Ce constructeur initialise chaque champ du `struct` aux valeurs par défaut. Pour plus d’informations, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md). Toutefois, ce constructeur sans paramètre est appelé uniquement si le `struct` est instancié avec `new`. Par exemple, ce code utilise le constructeur sans paramètre pour <xref:System.Int32>. Vous avez ainsi la garantie que l’entier est initialisé :  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Toutefois, le code suivant provoque une erreur de compilateur, car il n’utilise pas `new` et il essaie d’utiliser un objet qui n’a pas été initialisé :  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Les objets basés sur des `structs` (notamment tous les types numériques intégrés) peuvent également être initialisés ou assignés, puis utilisés, comme dans l’exemple suivant :  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 L’appel du constructeur sans paramètre pour un type valeur n’est donc pas obligatoire.  
  
 Les classes et les `structs` peuvent tous les deux définir des constructeurs qui prennent des paramètres. Les constructeurs qui prennent des paramètres doivent être appelés à l’aide d’une instruction `new` ou d’une instruction [base](../../../csharp/language-reference/keywords/base.md). Les classes et les `structs` peuvent également définir plusieurs constructeurs, et ni les classes ni les structs ne sont nécessaires pour définir un constructeur sans paramètre. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Cette classe peut être créée à l’aide de l’une ou l’autre des instructions suivantes :  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d’une classe de base. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur ne soit exécuté. Le mot clé `base` peut être utilisé avec ou sans paramètres. Tous les paramètres du constructeur peuvent être utilisés comme paramètres pour `base` ou comme partie d’une expression. Pour plus d’informations, consultez [base](../../../csharp/language-reference/keywords/base.md).  
  
 Dans une classe dérivée, si un constructeur de classe de base n’est pas appelé explicitement à l’aide du mot clé `base`, le constructeur sans paramètre, s’il existe, est appelé implicitement. Cela signifie que les déclarations de constructeur suivantes sont en fait les mêmes :  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Si une classe de base n’offre pas de constructeur sans paramètre, la classe dérivée doit faire un appel explicite à un constructeur de base à l’aide de `base`.  
  
 Un constructeur peut appeler un autre constructeur dans le même objet à l’aide du mot clé [this](../../../csharp/language-reference/keywords/this.md). Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles comme paramètres pour `this` ou comme partie d’une expression. Par exemple, le deuxième constructeur de l’exemple précédent peut être récrit à l’aide de `this` :  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 L’utilisation du mot clé `this` dans l’exemple précédent provoque l’appel de ce constructeur :  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Les constructeurs peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) ou [private protected](../../../csharp/language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent construire la classe. Pour plus d’informations, consultez la page [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Un constructeur peut être déclaré statique à l’aide du mot clé [static](../../../csharp/language-reference/keywords/static.md). Les constructeurs statiques sont appelés automatiquement, juste avant que des champs statiques soient accessibles, et ils sont généralement utilisés pour initialiser des membres de classe statique. Pour plus d’informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Constructeurs d’instances](~/_csharplang/spec/classes.md#instance-constructors) et [Constructeurs statiques](~/_csharplang/spec/classes.md#static-constructors) dans la [spécification du langage C#](../../language-reference/language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
