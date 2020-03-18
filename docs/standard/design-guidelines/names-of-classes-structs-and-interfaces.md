---
title: Noms de classes, de structures et d'interfaces
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400595"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="45ba3-102">Noms de classes, de structures et d'interfaces</span><span class="sxs-lookup"><span data-stu-id="45ba3-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="45ba3-103">Les lignes directrices de nommage qui suivent s’appliquent à la dénomination générale de type.</span><span class="sxs-lookup"><span data-stu-id="45ba3-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="45ba3-104">✔️ DO classes de noms et structs avec des noms ou des phrases de nom, en utilisant PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="45ba3-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="45ba3-105">Cela distingue les noms de type des méthodes, qui sont nommés avec des phrases verbe.</span><span class="sxs-lookup"><span data-stu-id="45ba3-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="45ba3-106">✔️ ne noms interfaces avec des phrases adjectifs, ou parfois avec des noms ou des phrases de nom.</span><span class="sxs-lookup"><span data-stu-id="45ba3-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="45ba3-107">Les noms et les phrases de nom doivent être utilisés rarement et ils pourraient indiquer que le type doit être une classe abstraite, et non une interface.</span><span class="sxs-lookup"><span data-stu-id="45ba3-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="45ba3-108">❌NE PAS donner aux noms de classe un préfixe (p. ex., « C »).</span><span class="sxs-lookup"><span data-stu-id="45ba3-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="45ba3-109">✔️ CONSIDER terminant le nom des classes dérivées avec le nom de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="45ba3-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="45ba3-110">C’est très lisible et explique clairement la relation.</span><span class="sxs-lookup"><span data-stu-id="45ba3-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="45ba3-111">Quelques exemples de cela `ArgumentOutOfRangeException`dans le code `Exception`sont: , qui est une sorte de , et `SerializableAttribute`, qui est une sorte de `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="45ba3-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="45ba3-112">Toutefois, il est important d’utiliser un jugement raisonnable pour appliquer cette directive; par exemple, `Button` la classe `Control` est une `Control` sorte d’événement, bien qu’il n’apparaît pas en son nom.</span><span class="sxs-lookup"><span data-stu-id="45ba3-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="45ba3-113">✔️ ne noms d’interface préfixe avec la lettre I, pour indiquer que le type est une interface.</span><span class="sxs-lookup"><span data-stu-id="45ba3-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="45ba3-114">Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression `IPersistable` de nom) et (adjectif) sont des noms d’interface appropriés.</span><span class="sxs-lookup"><span data-stu-id="45ba3-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="45ba3-115">Comme avec d’autres noms de type, évitez les abréviations.</span><span class="sxs-lookup"><span data-stu-id="45ba3-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="45ba3-116">✔️ assurez-vous que les noms diffèrent uniquement par le préfixe " I " sur le nom de l’interface lorsque vous définissez une paire de classe-interface où la classe est une implémentation standard de l’interface.</span><span class="sxs-lookup"><span data-stu-id="45ba3-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="45ba3-117">Noms des paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="45ba3-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="45ba3-118">Des génériques ont été ajoutés à .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="45ba3-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="45ba3-119">La fonctionnalité a introduit un nouveau type d’identifiant appelé *paramètre*de type .</span><span class="sxs-lookup"><span data-stu-id="45ba3-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="45ba3-120">✔️ NE nomment des paramètres de type générique avec des noms descriptifs à moins qu’un nom d’une seule lettre ne soit complètement explicite et qu’un nom descriptif n’ajoute pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="45ba3-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="45ba3-121">✔️ CONSIDER en `T` utilisant comme nom de paramètre de type pour les types avec un paramètre de type une seule lettre.</span><span class="sxs-lookup"><span data-stu-id="45ba3-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="45ba3-122">✔️ DO prefix noms de paramètres descriptifs avec `T`.</span><span class="sxs-lookup"><span data-stu-id="45ba3-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="45ba3-123">✔️ CONSIDER indiquant les contraintes imposées à un paramètre de type au nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="45ba3-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="45ba3-124">Par exemple, un paramètre contraint à `ISession` pourrait être appelé `TSession`.</span><span class="sxs-lookup"><span data-stu-id="45ba3-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="45ba3-125">Noms des types communs</span><span class="sxs-lookup"><span data-stu-id="45ba3-125">Names of Common Types</span></span>
 <span data-ttu-id="45ba3-126">✔️ NE suivent les lignes directrices décrites dans le tableau suivant lorsque vous nommez des types dérivés ou mettant en œuvre certains types de cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="45ba3-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="45ba3-127">Base Type</span><span class="sxs-lookup"><span data-stu-id="45ba3-127">Base Type</span></span>|<span data-ttu-id="45ba3-128">Ligne directrice de type dérivé/mise en œuvre</span><span class="sxs-lookup"><span data-stu-id="45ba3-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="45ba3-129">✔️ NE ajouter le suffixe "Attribut" aux noms des classes d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="45ba3-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="45ba3-130">✔️ NE ajouter le suffixe "EventHandler" aux noms des délégués qui sont utilisés dans les événements.</span><span class="sxs-lookup"><span data-stu-id="45ba3-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="45ba3-131">✔️ NE ajouter le suffixe "Callback" aux noms des délégués autres que ceux utilisés comme gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="45ba3-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="45ba3-132">❌NE PAS ajouter le suffixe "Délégué" à un délégué.</span><span class="sxs-lookup"><span data-stu-id="45ba3-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="45ba3-133">✔️ NE ajouter le suffixe "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="45ba3-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="45ba3-134">❌NE pas dériver de cette classe; utiliser le mot clé pris en charge par votre langue à la place; par exemple, dans le `enum` mot-clé C, utilisez le mot-clé.</span><span class="sxs-lookup"><span data-stu-id="45ba3-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="45ba3-135">❌NE PAS ajouter le suffixe "Enum" ou "Flag".</span><span class="sxs-lookup"><span data-stu-id="45ba3-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="45ba3-136">✔️ NE ajouter le suffixe "Exception.".</span><span class="sxs-lookup"><span data-stu-id="45ba3-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="45ba3-137">✔️ NE ajouter le suffixe "Dictionnaire."</span><span class="sxs-lookup"><span data-stu-id="45ba3-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="45ba3-138">Notez `IDictionary` qu’il s’agit d’un type spécifique de collection, mais cette ligne directrice prime sur la ligne directrice des collections plus générales qui suit.</span><span class="sxs-lookup"><span data-stu-id="45ba3-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="45ba3-139">✔️ NE ajouter le suffixe "Collection".</span><span class="sxs-lookup"><span data-stu-id="45ba3-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="45ba3-140">✔️ NE ajouter le suffixe "Stream".</span><span class="sxs-lookup"><span data-stu-id="45ba3-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="45ba3-141">✔️ N’ajoutez pas le suffixe "Permission".</span><span class="sxs-lookup"><span data-stu-id="45ba3-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="45ba3-142">Nommer les énumérations</span><span class="sxs-lookup"><span data-stu-id="45ba3-142">Naming Enumerations</span></span>
 <span data-ttu-id="45ba3-143">Les noms des types d’énumération (également appelés enums) en général doivent suivre les règles standard de nommage de type (PascalCasing, etc.).</span><span class="sxs-lookup"><span data-stu-id="45ba3-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="45ba3-144">Cependant, il existe d’autres lignes directrices qui s’appliquent spécifiquement aux enums.</span><span class="sxs-lookup"><span data-stu-id="45ba3-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="45ba3-145">✔️ NE pas utiliser un nom de type singulier pour un recensement à moins que ses valeurs sont des champs bits.</span><span class="sxs-lookup"><span data-stu-id="45ba3-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="45ba3-146">✔️ NE utiliser un nom de type pluriel pour un recensement avec des champs bits comme valeurs, également appelé drapeaux enum.</span><span class="sxs-lookup"><span data-stu-id="45ba3-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="45ba3-147">❌NE PAS utiliser un suffixe "Enum" dans les noms de type enum.</span><span class="sxs-lookup"><span data-stu-id="45ba3-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="45ba3-148">❌NE PAS utiliser "Flag" ou "Flags" suffixes dans les noms de type enum.</span><span class="sxs-lookup"><span data-stu-id="45ba3-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="45ba3-149">❌NE PAS utiliser un préfixe sur les noms de valeur de recensement (p. ex., « annonce » pour les enums ADO, « rtf » pour les enums de texte riches, etc.).</span><span class="sxs-lookup"><span data-stu-id="45ba3-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="45ba3-150">*Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="45ba3-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="45ba3-151">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="45ba3-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="45ba3-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45ba3-152">See also</span></span>

- [<span data-ttu-id="45ba3-153">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45ba3-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="45ba3-154">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="45ba3-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
