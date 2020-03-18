---
title: Versioning avec les mots clés override et new - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 089d5d7c7a95e2de4629f53255d9d9790fd5508a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705390"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Versioning avec les mots clés override et new (Guide de programmation C#)
Le langage C# est conçu de telle sorte que la gestion de version entre les classes de [base](../../language-reference/keywords/base.md) et les classes dérivées dans différentes bibliothèques puisse évoluer et préserver une compatibilité descendante. Cela signifie, par exemple, que l’introduction dans une [classe](../../language-reference/keywords/class.md) de base d’un nouveau membre portant le même nom qu’un membre dans une classe dérivée est totalement prise en charge par C# et n’engendre pas de comportement imprévisible. Cela signifie également qu'une classe doit indiquer de façon explicite si une méthode est conçue pour se substituer à une méthode héritée ou s'il s'agit d'une nouvelle méthode qui masque une méthode héritée portant un nom similaire.  
  
 Dans C#, les classes dérivées peuvent contenir des méthodes portant le même nom que des méthodes de classe de base.  
  
- La méthode de classe de base doit être définie comme [virtuelle](../../language-reference/keywords/virtual.md).  
  
- Si la méthode dans la classe dérivée n’est pas précédée des mots clés [new](../../language-reference/keywords/new-modifier.md) ou [override](../../language-reference/keywords/override.md), le compilateur émet un avertissement et la méthode se comporte comme si le mot clé `new` était présent.  
  
- Si la méthode dans la classe dérivée est précédée du mot clé `new`, la méthode est définie comme étant indépendante de la méthode dans la classe de base.  
  
- Si la méthode dans la classe dérivée est précédée du mot clé `override`, les objets de la classe dérivée appelleront cette méthode plutôt que la méthode de la classe de base.  
  
- La méthode de la classe de base peut être appelée à partir de la classe dérivée à l’aide du mot clé `base`.  
  
- Les mots clés `override`, `virtual` et `new` peuvent également être appliqués aux propriétés, indexeurs et événements.  
  
 Par défaut, les méthodes C# ne sont pas virtuelles. Si une méthode est déclarée comme virtuelle, toute classe héritant de la méthode peut implémenter sa propre version. Pour créer une méthode virtuelle, le modificateur `virtual` est utilisé dans la déclaration de méthode de la classe de base. La classe dérivée peut ensuite remplacer la méthode virtuelle de base avec le mot clé `override` ou masquer la méthode virtuelle dans la classe de base avec le mot clé `new`. Si ni le mot clé `override` ni le mot clé `new` ne sont spécifiés, le compilateur émettra un avertissement et la méthode dans la classe dérivée masquera la méthode dans la classe de base.  
  
 Pour illustrer ceci dans un exemple pratique, supposons un instant que la Société A ait créé une classe nommée `GraphicsClass` que votre programme utilise. Les éléments suivants représentent `GraphicsClass` :  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Votre société utilise cette classe, et vous l’utilisez pour dériver votre propre classe, en ajoutant une nouvelle méthode :  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Votre application est utilisée sans problèmes, jusqu’à ce que la Société A publie une nouvelle version de `GraphicsClass`, qui ressemble au code suivant :  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 La nouvelle version de `GraphicsClass` contient maintenant une méthode nommée `DrawRectangle`. Initialement, rien ne se produit. La nouvelle version est encore compatible au format binaire avec l’ancienne version. Tous les logiciels que vous avez déployés continueront de fonctionner, même si la nouvelle classe est installée sur ces systèmes informatiques. Tout appel existant à la méthode `DrawRectangle` continuera de faire référence à votre version, dans votre classe dérivée.  
  
 Toutefois, dès que vous recompilerez votre application à l’aide de la nouvelle version de `GraphicsClass`, vous recevrez un avertissement du compilateur, CS0108. Cet avertissement vous informe que vous devez envisager la façon dont vous souhaitez que votre méthode `DrawRectangle` se comporte dans votre application.  
  
 Si vous souhaitez que votre méthode remplace la nouvelle méthode de la classe de base, utilisez le mot clé `override` :  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Le mot clé `override` garantit que tous les objets dérivés de `YourDerivedGraphicsClass` utiliseront la version de classe dérivée de `DrawRectangle`. Les objets dérivés de `YourDerivedGraphicsClass` peuvent toujours accéder à la version de la classe de base de `DrawRectangle` à l’aide du mot clé base :  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Si vous ne souhaitez pas que votre méthode se substitue à la nouvelle méthode de la classe de base, prenez en compte les considérations suivantes. Pour éviter toute confusion entre les deux méthodes, vous pouvez renommer votre méthode. Ceci peut prendre du temps et constituer un risque d’erreur ou bien ne pas être tout simplement pratique dans certains cas. Toutefois, si votre projet est relativement petit, vous pouvez utiliser les options de refactorisation de Visual Studio pour renommer la méthode. Pour plus d’informations, consultez [Refactorisation des classes et des types (Concepteur de classes)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Sinon, vous pouvez éviter de recevoir l’avertissement à l’aide du mot clé `new` dans la définition de votre classe dérivée :  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 L’utilisation du mot clé `new` indique au compilateur que votre définition masque la définition qui est contenue dans la classe de base. Il s'agit du comportement par défaut.  
  
## <a name="override-and-method-selection"></a>Substitution et sélection de méthode  
 Lorsqu'une méthode est appelée sur une classe, le compilateur C# sélectionne la meilleure méthode à appeler si plusieurs méthodes sont compatibles avec l'appel, comme lorsque deux méthodes portent les mêmes noms et dont les paramètres sont compatibles avec les paramètres transmis. Les méthodes suivantes seraient compatibles :  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Quand `DoWork` est appelée sur une instance de `Derived`, le compilateur C# essaie d’abord de rendre l’appel compatible avec les versions de `DoWork` déclarées à l’origine sur `Derived`. Les méthodes override ne sont pas considérées comme déclarées sur une classe ; il s’agit de nouvelles implémentations d’une méthode déclarée sur une classe de base. Le compilateur C# essaiera de faire correspondre l’appel à une méthode substituée portant le même nom et avec des paramètres compatibles uniquement s’il ne parvient pas à faire correspondre l’appel de méthode à une méthode d’origine sur `Derived`. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Étant donné que la variable `val` peut être convertie implicitement en un double, le compilateur C# appelle `DoWork(double)` au lieu de `DoWork(int)`. Il existe deux façons d’éviter ceci. Premièrement, évitez de déclarer de nouvelles méthodes portant le même nom que des méthodes virtuelles. Deuxièmement, vous pouvez indiquer au compilateur C# d’appeler la méthode virtuelle en le faisant chercher dans la liste de méthodes de la classe de base par casting de l’instance `Derived` en `Base`. Étant donné que la méthode est virtuelle, l’implémentation de `DoWork(int)` sur `Derived` sera appelée. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Pour obtenir d’autres exemples des mots clés `new` et `override`, consultez [Savoir quand utiliser les mots clés override et new](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Méthodes](./methods.md)
- [Héritage](./inheritance.md)
