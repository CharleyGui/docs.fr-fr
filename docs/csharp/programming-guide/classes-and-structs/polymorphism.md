---
title: Polymorphisme - Guide de programmation C#
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170167"
---
# <a name="polymorphism-c-programming-guide"></a>Polymorphisme (Guide de programmation C#)

Le polymorphisme est souvent considéré comme le troisième pilier d'une programmation orientée objet, après l'encapsulation et l'héritage. Le polymorphisme est le mot grec qui signifie « plusieurs formes » et il prend deux aspects distincts :
  
- Au moment de l’exécution, les objets d’une classe dérivée peuvent être traités comme des objets d’une classe de base dans les paramètres de méthode et les collections ou les tableaux. Lorsque ce polymorphisme se produit, le type déclaré de l’objet n’est plus identique à son type de temps d’exécution.
- Les classes de base peuvent définir et mettre en œuvre des *méthodes* [virtuelles,](../../language-reference/keywords/virtual.md) et les classes dérivées peuvent les [remplacer,](../../language-reference/keywords/override.md) ce qui signifie qu’elles fournissent leur propre définition et mise en œuvre. Au moment de l'exécution, quand le code client appelle la méthode, le CLR recherche le type au moment de l'exécution et appelle cette substitution de la méthode virtuelle. Dans votre code source, vous pouvez appeler une méthode sur une classe de base, et provoquer une version d’une classe dérivée de la méthode à exécuter.

Les méthodes virtuelles vous permettent d'utiliser des groupes d'objets liés de façon uniforme. Par exemple, si vous avez une application de dessin qui permet à un utilisateur de créer différents types de formes sur une surface de dessin. Vous ne savez pas au moment de la compilation les types de formes spécifiques que l'utilisateur va créer. Cependant, l'application doit conserver une trace des différents types de formes créés et les mettre à jour en réponse aux actions de la souris. Vous pouvez utiliser le polymorphisme pour résoudre ce problème en deux étapes :

1. Créer une hiérarchie de classe dans laquelle chaque classe de forme dérive d'une classe de base commune.
1. Utiliser une méthode virtuelle pour appeler la méthode appropriée dans une classe dérivée via un seul appel à la méthode de classe de base.

Tout d'abord, créez une classe de base appelée `Shape`, et des classes dérivées telles que `Rectangle`, `Circle`, et `Triangle`. Donnez à la classe `Shape` une méthode virtuelle appelée `Draw`, et substituez-la dans chaque classe dérivée pour dessiner une forme spécifique représentée par la classe. Créez `List<Shape>` un objet `Circle`et `Triangle`ajoutez `Rectangle` un , , et à elle.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Pour mettre à jour la surface de dessin, utilisez une boucle [foreach](../../language-reference/keywords/foreach-in.md) pour l’itération dans la liste et appelez la méthode `Draw` sur chaque objet `Shape` de la liste. Même si chaque objet de la `Shape`liste a un type déclaré de , c’est le type de temps d’exécution (la version dépassée de la méthode dans chaque classe dérivée) qui sera invoquée.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

En C#, chaque type est polymorphique, car tous les types, y compris les types définis par l'utilisateur, héritent de <xref:System.Object>.  

## <a name="polymorphism-overview"></a>Aperçu du polymorphisme

### <a name="virtual-members"></a>Membres virtuels

Lorsqu’une classe dérivée d’une classe de base, elle gagne toutes les méthodes, champs, propriétés et événements de la classe de base. Le concepteur de la classe dérivée peut différents choix pour le comportement des méthodes virtuelles:

- La classe dérivée peut remplacer les membres virtuels dans la classe de base, définissant un nouveau comportement.
- La classe dérivée hérite de la méthode de classe de base la plus proche sans la remplacer, en préservant le comportement existant, mais en permettant à d’autres classes dérivées de passer outre à la méthode.
- La classe dérivée peut définir une nouvelle implémentation non virtuelle des membres qui cachent les implémentations de la classe de base.

Une classe dérivée ne peut substituer un membre de classe de base que si le membre de classe de base est déclaré comme étant [virtual](../../language-reference/keywords/virtual.md) ou [abstract](../../language-reference/keywords/abstract.md). Le membre dérivé doit utiliser le mot clé [override](../../language-reference/keywords/override.md) pour indiquer explicitement que la méthode est conçue pour participer à l’appel virtuel. Le code suivant est fourni à titre d'exemple :

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Les champs ne peuvent pas être virtuels; seules les méthodes, les propriétés, les événements et les indexateurs peuvent être virtuels. Quand une classe dérivée est substituée à un membre virtuel, ce membre est appelé lors de l'accès à une instance de cette classe en tant qu'instance de la classe de base. Le code suivant est fourni à titre d'exemple :

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Les méthodes et propriétés virtuelles permettent aux classes dérivées d'étendre une classe de base sans avoir besoin d'utiliser l'implémentation de classe de base d'une méthode. Pour plus d’informations, consultez [Versioning avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md). Une interface fournit un autre moyen pour définir une méthode ou un ensemble de méthodes dont l'implémentation est confiée aux classes dérivées. Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).

### <a name="hide-base-class-members-with-new-members"></a>Masquer les membres de la classe de base avec de nouveaux membres

Si vous voulez que votre classe dérivée ait un membre du même nom qu’un membre dans une classe de base, vous pouvez utiliser le [nouveau](../../language-reference/keywords/new-modifier.md) mot clé pour masquer le membre de la classe de base. Le mot clé `new` est placé avec le type de retour d'un membre de classe qui est remplacé. Le code suivant est fourni à titre d'exemple :

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Les membres cachés de la classe de base peuvent être consultés à partir du code client en jetant l’instance de la classe dérivée à une instance de la classe de base. Par exemple :

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Empêcher les classes dérivées de prépondérer les membres virtuels  

Les membres virtuels restent virtuels, quel que soit le nombre de classes déclarées entre le membre virtuel et la classe qui l’avait déclaré à l’origine. Si `A` la classe déclare un `B` membre virtuel, et la classe dérive `A`de , et la classe `C` dérive de `B`, la classe `C` hérite du membre virtuel, et peut l’emporter, indépendamment de savoir si la classe `B` a déclaré un remplacement pour ce membre. Le code suivant est fourni à titre d'exemple :

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Une classe dérivée peut arrêter l’héritage virtuel en déclarant une substitution comme étant [sealed](../../language-reference/keywords/sealed.md). L’arrêt de `sealed` l’héritage nécessite de placer le mot clé avant le `override` mot clé dans la déclaration du membre de la classe. Le code suivant est fourni à titre d'exemple :

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

Dans l’exemple précédent, la méthode `DoWork` n’est `C`plus virtuelle à aucune classe dérivée de . Il est toujours virtuel `C`pour les cas de , `B` même `A`si elles sont coulées pour taper ou taper . Les méthodes scellées peuvent être remplacées par des classes dérivées en utilisant le `new` mot clé, comme le montre l’exemple suivant :

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

Dans ce cas, `DoWork` si `D` on appelle `D`à l’aide d’une variable de type, le nouveau `DoWork` est appelé. Si une variable `C` `B`de `A` type , , ou `D`est utilisé `DoWork` pour accéder à une instance de , un `DoWork` appel `C`à suivre les règles de l’héritage virtuel, routage de ces appels à la mise en œuvre de la classe .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Accédez aux membres virtuels de la classe de base des classes dérivées

Une classe dérivée qui a remplacé ou écrasé une méthode ou une propriété peut encore accéder à la méthode ou à la propriété dans la classe de base avec le mot clé `base`. Le code suivant est fourni à titre d'exemple :

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

Pour plus d’informations, consultez [base](../../language-reference/keywords/base.md).

> [!NOTE]
> Il est recommandé que les membres virtuels utilisent `base` pour appeler l'implémentation de classe de base de ce membre dans leur propre implémentation. L'exécution du comportement de classe de base permet à la classe dérivée de se concentrer sur l'implémentation du comportement spécifique à la classe dérivée. Si l'implémentation de classe de base n'est pas appelée, la classe dérivée doit rendre son comportement compatible avec le comportement de la classe de base.

## <a name="in-this-section"></a>Contenu de cette section

- [Gestion de version avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md)
- [Savoir quand utiliser les mots clés override et new](./knowing-when-to-use-override-and-new-keywords.md)
- [Comment remplacer la méthode ToString](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Héritage](./inheritance.md)
- [Classes abstract et sealed et membres de classe](./abstract-and-sealed-classes-and-class-members.md)
- [Méthodes](./methods.md)
- [Événements](../events/index.md)
- [Propriétés](./properties.md)
- [Indexeurs](../indexers/index.md)
- [Types](../types/index.md)
