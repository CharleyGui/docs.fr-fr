---
title: Programmation orientée objet (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 50b38833582ebe46836ccfab4e1ebeb98b53a96e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659878"
---
# <a name="object-oriented-programming-c"></a>Programmation orientée objet (C#)

C# offre une prise en charge complète de la programmation orientée objet, y compris l’encapsulation, l’héritage et le polymorphisme.

L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.

L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.

Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.

Cette section décrit les concepts suivants :

- [Classes et objets](#Classes)

  - [Membres de classe](#Members)

    - [Propriétés et champs](#Properties)

    - [Méthodes](#Methods)

    - [Constructeurs](#Constructors)

    - [Finaliseurs](#Finalizers)

    - [Événements](#Events)

    - [Classes imbriquées](#NestedClasses)

  - [Modificateurs d’accès et niveaux d’accès](#AccessModifiers)

  - [Instanciation de classes](#InstantiatingClasses)

  - [Classes et membres statiques](#Static)

  - [Types anonymes](#AnonymousTypes)

- [Héritage](#Inheritance)

  - [Substitution de membres](#Overriding)

- [Interfaces](#Interfaces)

- [Génériques](#Generics)

- [Délégués](#Delegates)

## <a name="Classes"></a> Classes et objets

Les termes *classe* et *objet* sont parfois employés indifféremment, mais en réalité, les classes décrivent le *type* des objets, alors que les objets sont des *instances* utilisables des classes. Cela explique pourquoi l’opération de création d’un objet est appelée *instanciation*. Si l'on reprend l'analogie avec un plan de construction, une classe est un plan, et un objet est un bâtiment construit à partir de ce plan.

Pour définir une classe :

```csharp
class SampleClass
{
}
```

C# fournit également une version basique de classes, appelée *structures*, qui sont utiles pour créer un grand tableau d’objets sans utiliser trop de mémoire pour cette opération.

Pour définir une structure :

```csharp
struct SampleStruct
{
}
```

Pour plus d'informations, voir :

- [class](../../language-reference/keywords/class.md)

- [struct](../../language-reference/keywords/struct.md)

### <a name="Members"></a> Membres de classe

Chaque classe peut avoir différents *membres de classe* : des propriétés qui décrivent les données de classe, des méthodes qui définissent le comportement de classe et des événements qui permettent la communication entre les différents objets et classes.

#### <a name="Properties"></a> Propriétés et champs

Les propriétés et les champs sont des informations contenues dans un objet. Les champs sont similaires aux variables, car ils peuvent être lus ou définis directement.

Pour définir un champ :

```csharp
class SampleClass
{
    public string sampleField;
}
```

Les propriétés comportent des procédures Get et Set qui apportent davantage de contrôle sur le mode de définition ou de retour des valeurs.

C# vous permet de créer un champ privé pour le stockage de la valeur de propriété, ou d’utiliser des propriétés implémentées automatiquement qui créent ce champ de façon automatique en arrière-plan et fournissent la logique de base des procédures de propriété.

Pour définir une propriété implémentée automatiquement :

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Si vous devez exécuter des opérations supplémentaires pour la lecture et l'écriture de la valeur de propriété, définissez un champ pour le stockage de la valeur de propriété et fournissez la logique de base pour son stockage et son extraction :

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

La plupart des propriétés disposent de méthodes ou de procédures destinées à la fois à définir et à obtenir la valeur de propriété. Toutefois, vous pouvez créer des propriétés en lecture seule ou en écriture seule pour empêcher qu'elles soient modifiées ou lues. En C#, vous pouvez omettre la méthode de propriété `get` ou `set`. Toutefois, les propriétés implémentées automatiquement ne peuvent pas être en lecture seule ni en écriture seule.

Pour plus d'informations, voir :

- [get](../../language-reference/keywords/get.md)

- [set](../../language-reference/keywords/set.md)

#### <a name="Methods"></a> Méthodes

Une *méthode* correspond à une action qu’un objet peut effectuer.

Pour définir une méthode de classe :

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Une classe peut avoir plusieurs implémentations, ou *surcharges*, de la même méthode qui diffèrent du point de vue du nombre de paramètres ou des types de paramètres.

Pour surcharger une méthode :

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

Dans la plupart des cas, vous déclarez une méthode dans une définition de classe. Toutefois, C# prend également en charge des *méthodes d’extension*, qui vous permettent d’ajouter des méthodes à une classe existante hors de la définition réelle de la classe.

Pour plus d'informations, voir :

- [Méthodes](../classes-and-structs/methods.md)

- [Méthodes d’extension](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> Constructeurs

Les constructeurs sont des méthodes de classe qui s'exécutent automatiquement lorsqu'un objet d'un type donné est créé. Les constructeurs initialisent habituellement les données membres du nouvel objet. Un constructeur ne peut s'exécuter qu'une seule fois lorsqu'une classe est créée. En outre, le code figurant dans le constructeur s'exécute toujours avant tout autre code dans une classe. Toutefois, vous pouvez créer plusieurs surcharges de constructeur de la même façon que vous le faites pour toute autre méthode.

Pour définir un constructeur pour une classe :

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Pour plus d'informations, voir :

[Constructeurs](../classes-and-structs/constructors.md).

#### <a name="Finalizers"></a> Finaliseurs

Les finaliseurs permettent de détruire des instances de classes. Dans le .NET Framework, le garbage collector gère automatiquement l'allocation et la libération de mémoire pour les objets managés figurant dans votre application. Toutefois, vous pouvez avoir besoin de finaliseurs pour nettoyer toutes les ressources non managées créées par votre application. Il ne peut y avoir qu'un seul finaliseur pour une même classe.

Pour plus d’informations sur les finaliseurs et l’opération de garbage collection dans le .NET Framework, consultez [Garbage collection](../../../standard/garbage-collection/index.md).

#### <a name="Events"></a> Événements

Les événements permettent à une classe ou un objet de notifier d'autres classes ou objets lorsqu'une situation intéressante se produit. La classe qui envoie (ou déclenche) l’événement est appelée *éditeur* et les classes qui reçoivent (ou gèrent) l’événement sont appelées *abonnés*. Pour plus d’informations sur les événements, leur déclenchement et leur gestion, consultez [Événements](../../../standard/events/index.md).

- Pour déclarer un événement dans une classe, utilisez le mot clé [event](../../language-reference/keywords/event.md).

- Pour déclencher un événement, appelez le délégué d'événement.

- Pour vous abonner à un événement, utilisez l'opérateur `+=` ; pour annuler un abonnement à un événement, utilisez l'opérateur `-=`.

#### <a name="NestedClasses"></a> Classes imbriquées

Une classe définie à l’intérieur d’une autre classe est dite *imbriquée*. Par défaut, une classe imbriquée est privée.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Pour créer une instance de la classe imbriquée, utilisez le nom de la classe de conteneur suivi d'un point, puis du nom de la classe imbriquée :

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> Modificateurs d’accès et niveaux d’accès

Toutes les classes et tous les membres de classe peuvent spécifier le niveau d’accès qu’ils fournissent aux autres classes à l’aide des *modificateurs d’accès*.

Les modificateurs d’accès suivants sont disponibles :

|Modificateur C#|Définition|
|------------------|----------------|
|[public](../../language-reference/keywords/public.md)|Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.|
|[private](../../language-reference/keywords/private.md)|Seul le code de la même classe peut accéder au type ou au membre.|
|[protected](../../language-reference/keywords/protected.md)|Seul le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre.|
|[internal](../../language-reference/keywords/internal.md)|Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|Tout code du même assembly ou toute classe dérivée dans un autre assembly peut accéder au type ou au membre.|
|[private protected](../../language-reference/keywords/private-protected.md)|Le code de la même classe ou d'une classe dérivée peut accéder au type ou au membre dans l’assembly de la classe de base.|

Pour plus d’informations, consultez la page [Modificateurs d’accès](../classes-and-structs/access-modifiers.md).

### <a name="InstantiatingClasses"></a> Instanciation de classes

Pour créer un objet, vous devez instancier une classe ou créer une instance de classe.

```csharp
SampleClass sampleObject = new SampleClass();
```

Après avoir instancié une classe, vous pouvez assigner des valeurs aux propriétés et champs de l'instance et appeler des méthodes de classe.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Pour assigner des valeurs aux propriétés pendant le processus d'instanciation de la classe, utilisez des initialiseurs d'objets :

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Pour plus d'informations, voir :

- [new, opérateur](../../language-reference/operators/new-operator.md)

- [Initialiseurs d’objets et de collections](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> Classes et membres statiques

Un membre statique de la classe est une propriété, une procédure ou un champ que toutes les instances d’une classe partagent.

Pour définir un membre statique :

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Pour accéder au membre statique, utilisez le nom de la classe sans créer d’objet de cette classe :

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Les classes statiques dans C# ont uniquement des membres statiques et ne peuvent pas être instanciées. Les membres statiques ne peuvent pas non plus accéder aux propriétés, champs ou méthodes non statiques

Pour plus d’informations, consultez [static](../../language-reference/keywords/static.md).

### <a name="AnonymousTypes"></a> Types anonymes

Les types anonymes vous permettent de créer des objets sans écrire de définition de classe pour le type de données. À la place, le compilateur se charge de générer une classe. La classe ne possède pas de nom utilisable et contient les propriétés que vous spécifiez lors de la déclaration de l'objet.

Pour créer une instance de type anonyme :

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Pour plus d'informations, voir : [Types anonymes](../classes-and-structs/anonymous-types.md).

## <a name="Inheritance"></a> Héritage

Il vous permet de créer une nouvelle classe qui réutilise, étend et modifie le comportement défini dans une autre classe. La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*. Toutefois, toutes les classes dans C# héritent implicitement de la classe <xref:System.Object> qui prend en charge la hiérarchie de classes .NET et fournit des services de bas niveau à toutes les classes.

> [!NOTE]
> C# ne prend pas en charge l’héritage multiple. Vous pouvez donc spécifier une seule classe de base pour une classe dérivée.

Pour hériter d'une classe de base :

```csharp
class DerivedClass:BaseClass {}
```

Par défaut, toutes les classes peuvent être héritées. Toutefois, vous pouvez spécifier si une classe ne doit pas être utilisée comme classe de base ou créer une classe qui peut être utilisée uniquement comme classe de base.

Pour spécifier qu'une classe ne peut pas être utilisée comme classe de base :

```csharp
public sealed class A { }
```

Pour spécifier qu'une classe peut être utilisée uniquement comme classe de base et ne peut pas être instanciée :

```csharp
public abstract class B { }
```

Pour plus d'informations, voir :

- [sealed](../../language-reference/keywords/sealed.md)

- [abstract](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a> Substitution de membres

Par défaut, une classe dérivée hérite de tous les membres de sa classe de base. Si vous souhaitez modifier le comportement du membre hérité, vous devez le substituer. Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode, de la propriété ou de l'événement dans la classe dérivée.

Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :

|Modificateur C#|Définition|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Autorise la substitution d'un membre de classe dans une classe dérivée.|
|[override](../../language-reference/keywords/override.md)|Substitue un membre virtuel (substituable) défini dans la classe de base.|
|[abstract](../../language-reference/keywords/abstract.md)|Requiert qu'un membre de classe soit substitué dans la classe dérivée.|
|[new, modificateur](../../language-reference/keywords/new-modifier.md)|Masque un membre hérité d'une classe de base.|

## <a name="Interfaces"></a> Interfaces

Tout comme les classes, les interfaces définissent un ensemble de propriétés, méthodes et événements. Cependant, contrairement aux classes, les interfaces n'assurent pas l'implémentation. Elles sont implémentées par les classes et définies en tant qu'entités distinctes des classes. Une interface représente un contrat, dans le sens où une classe qui implémente une interface doit implémenter tous les aspects de cette interface exactement telle qu'elle a été définie.

Pour définir une interface :

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Pour implémenter une interface dans une classe :

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Pour plus d'informations, voir :

[Interfaces](../interfaces/index.md)

[interface](../../language-reference/keywords/interface.md)

## <a name="Generics"></a> Génériques

Les classes, les structs, les interfaces et les méthodes dans le .NET Framework peuvent inclure des *paramètres de type*, qui définissent les types d’objets qu’ils peuvent stocker ou utiliser. L’exemple le plus commun de génériques est une collection dans laquelle vous pouvez spécifier le type d’objets à stocker dans une collection.

Pour définir une classe générique :

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Pour créer une instance de classe générique :

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Pour plus d'informations, voir :

- [Génériques](../../../standard/generics/index.md)

- [Génériques](../generics/index.md)

## <a name="Delegates"></a> Délégués

Un *délégué* est un type qui définit une signature de méthode et peut fournir une référence à toute méthode avec une signature compatible. Vous pouvez appeler la méthode par le biais du délégué. Les délégués sont utilisés pour passer des méthodes comme arguments à d'autres méthodes.

> [!NOTE]
> Les gestionnaires d'événements sont tout simplement des méthodes appelées par le biais de délégués. Pour plus d’informations sur l’utilisation de délégués dans la gestion des événements, consultez [Événements](../../../standard/events/index.md).

Pour créer un délégué :

```csharp
public delegate void SampleDelegate(string str);
```

Pour créer une référence à une méthode qui correspond à la signature spécifiée par le délégué :

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

Pour plus d'informations, voir :

- [Délégués](../delegates/index.md)

- [delegate](../../language-reference/keywords/delegate.md)

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
