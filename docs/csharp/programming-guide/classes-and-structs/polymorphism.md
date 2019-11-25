---
title: Polymorphisme - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: be075c358d9ca2c36b6d173fca983c16f6b0d78c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970339"
---
# <a name="polymorphism-c-programming-guide"></a>Polymorphisme (Guide de programmation C#)
Le polymorphisme est souvent considéré comme le troisième pilier d'une programmation orientée objet, après l'encapsulation et l'héritage. Le polymorphisme est le mot grec qui signifie « plusieurs formes » et il prend deux aspects distincts :  
  
- Au moment de l’exécution, les objets d’une classe dérivée peuvent être traités comme des objets d’une classe de base dans les paramètres de méthode et les collections ou les tableaux. Lorsque cela se passe, le type déclaré de l'objet n'est plus identique à son type au moment de l'exécution.  
  
- Les classes de base peuvent définir et implémenter des *méthodes* [virtuelles](../../language-reference/keywords/virtual.md), et les classes dérivées peuvent les [substituer](../../language-reference/keywords/override.md), ce qui signifie qu’elles fournissent leur propre définition et implémentation. Au moment de l'exécution, quand le code client appelle la méthode, le CLR recherche le type au moment de l'exécution et appelle cette substitution de la méthode virtuelle. C'est pourquoi, dans le code source vous pouvez appeler une méthode dans une classe de base, et provoquer l'exécution d'une version de la classe dérivée de la méthode.  
  
 Les méthodes virtuelles vous permettent d'utiliser des groupes d'objets liés de façon uniforme. Par exemple, si vous avez une application de dessin qui permet à un utilisateur de créer différents types de formes sur une surface de dessin. Vous ne savez pas au moment de la compilation les types de formes spécifiques que l'utilisateur va créer. Cependant, l'application doit conserver une trace des différents types de formes créés et les mettre à jour en réponse aux actions de la souris. Vous pouvez utiliser le polymorphisme pour résoudre ce problème en deux étapes :  
  
1. Créer une hiérarchie de classe dans laquelle chaque classe de forme dérive d'une classe de base commune.  
  
2. Utiliser une méthode virtuelle pour appeler la méthode appropriée dans une classe dérivée via un seul appel à la méthode de classe de base.  
  
 Tout d'abord, créez une classe de base appelée `Shape`, et des classes dérivées telles que `Rectangle`, `Circle`, et `Triangle`. Donnez à la classe `Shape` une méthode virtuelle appelée `Draw`, et substituez-la dans chaque classe dérivée pour dessiner une forme spécifique représentée par la classe. Créez un objet `List<Shape>` et ajoutez-lui un cercle, un triangle et un rectangle. Pour mettre à jour la surface de dessin, utilisez une boucle [foreach](../../language-reference/keywords/foreach-in.md) pour l’itération dans la liste et appelez la méthode `Draw` sur chaque objet `Shape` de la liste. Même si chaque objet de la liste a un type déclaré égal à `Shape`, il s'agit du type au moment de l'exécution (la version substituée de la méthode dans chaque classe dérivée) qui est appelé.  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 En C#, chaque type est polymorphique, car tous les types, y compris les types définis par l'utilisateur, héritent de <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Vue d'ensemble du polymorphisme  
  
### <a name="virtual-members"></a>Membres virtuels  
 Quand une classe dérivée hérite d'une classe de base, elle gagne toutes les méthodes, les champs, les propriétés et les événements de la classe de base. Le concepteur de la classe dérivée peut choisir  
  
- de substituer les membres virtuels dans la classe de base,  
  
- d'hériter de la méthode de classe de base la plus proche sans la substituer  
  
- de définir une nouvelle implémentation non virtuelle de ces membres qui masque les implémentations de la classe de base  
  
 Une classe dérivée ne peut substituer un membre de classe de base que si le membre de classe de base est déclaré comme étant [virtual](../../language-reference/keywords/virtual.md) ou [abstract](../../language-reference/keywords/abstract.md). Le membre dérivé doit utiliser le mot clé [override](../../language-reference/keywords/override.md) pour indiquer explicitement que la méthode est conçue pour participer à l’appel virtuel. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 Les champs ne peuvent pas être virtuels ; seuls les méthodes, propriétés, événements et indexeurs peuvent être virtuels. Quand une classe dérivée est substituée à un membre virtuel, ce membre est appelé lors de l'accès à une instance de cette classe en tant qu'instance de la classe de base. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 Les méthodes et propriétés virtuelles permettent aux classes dérivées d'étendre une classe de base sans avoir besoin d'utiliser l'implémentation de classe de base d'une méthode. Pour plus d’informations, consultez [Versioning avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md). Une interface fournit un autre moyen pour définir une méthode ou un ensemble de méthodes dont l'implémentation est confiée aux classes dérivées. Pour plus d’informations, consultez [Interfaces](../interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Masquage des membres de classe de base par de nouveaux membres  
 Si vous voulez que votre membre dérivé ait le même nom qu’un membre d’une classe de base, mais que vous ne voulez pas qu’il participe à l’appel virtuel, vous pouvez utiliser le mot clé [new](../../language-reference/keywords/new-modifier.md). Le mot clé `new` est placé avec le type de retour d'un membre de classe qui est remplacé. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 Les membres de classe de base masqués sont toujours accessibles à partir du code client en effectuant un cast de l'instance de la classe dérivée vers une instance de la classe de base. Exemple :  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Empêcher les classes dérivées de remplacer les membres virtuels  
 Les membres virtuels restent virtuels indéfiniment, quel que soit le nombre de classes déclarées entre le membre virtuel et la classe qui l'a déclaré à l'origine. Si la classe A déclare un membre virtuel, et la classe B dérive de A, et la classe C dérive de B, la classe C hérite du membre virtuel et peut le remplacer, que la classe B ait ou non déclarée une substitution pour ce membre. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 Une classe dérivée peut arrêter l’héritage virtuel en déclarant une substitution comme étant [sealed](../../language-reference/keywords/sealed.md). Cela nécessite l'ajout du mot clé `sealed` avant le mot clé `override` dans la déclaration de membre de classe. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 Dans l’exemple précédent, la méthode `DoWork` n’est plus virtuelle vis-à-vis des classes dérivées de C. Elle l’est toujours pour les instances de C, même si elles sont converties en type B ou A. Les méthodes sealed peuvent être remplacées par des classes dérivées à l’aide du mot clé `new`, comme le montre l’exemple suivant :  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 Dans ce cas, si `DoWork` est appelé sur D à l'aide d'une variable de type D, le nouveau `DoWork` est appelé. Si une variable de type C, B, ou A est utilisée pour accéder à une instance de D, un appel à `DoWork` suivra les règles de l'héritage virtuel, en routant ces appels vers l'implémentation de `DoWork` dans la classe C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Accès aux membres virtuels de la classe de base à partir de classes dérivées  
 Une classe dérivée qui a remplacé ou écrasé une méthode ou une propriété peut encore accéder à la méthode ou à la propriété dans la classe de base avec le mot clé `base`. Le code suivant est fourni à titre d'exemple :  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 Pour plus d’informations, consultez [base](../../language-reference/keywords/base.md).  
  
> [!NOTE]
> Il est recommandé que les membres virtuels utilisent `base` pour appeler l'implémentation de classe de base de ce membre dans leur propre implémentation. L'exécution du comportement de classe de base permet à la classe dérivée de se concentrer sur l'implémentation du comportement spécifique à la classe dérivée. Si l'implémentation de classe de base n'est pas appelée, la classe dérivée doit rendre son comportement compatible avec le comportement de la classe de base.  
  
## <a name="in-this-section"></a>Dans cette section  
  
- [Versioning avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md)  
  
- [Savoir quand utiliser les mots clés override et new](./knowing-when-to-use-override-and-new-keywords.md)  
  
- [Comment substituer la méthode ToString](./how-to-override-the-tostring-method.md)
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Héritage](./inheritance.md)
- [Classes abstract et sealed et membres de classe](./abstract-and-sealed-classes-and-class-members.md)
- [Méthodes](./methods.md)
- [Événements](../events/index.md)
- [Propriétés](./properties.md)
- [Indexeurs](../indexers/index.md)
- [Types](../types/index.md)
