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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353705"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="6a8bf-102">Noms de classes, de structures et d'interfaces</span><span class="sxs-lookup"><span data-stu-id="6a8bf-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="6a8bf-103">Les règles d’affectation des noms qui suivent s’appliquent à la dénomination générale des types.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="6a8bf-104">**✓ DO** un nom de classes et structs avec des noms ou des expressions nominales, à l’aide de la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="6a8bf-105">Cela distingue les noms de types des méthodes, qui sont nommées à l’aide d’expressions de verbe.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="6a8bf-106">**✓ DO** nom interfaces phrases adjectivales ou parfois avec des noms ou des expressions nominales.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="6a8bf-107">Les noms et les expressions nominales doivent être utilisés rarement et peuvent indiquer que le type doit être une classe abstraite, et non une interface.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="6a8bf-108">**X DO NOT** donner des noms de classe un préfixe (par exemple, « C »).</span><span class="sxs-lookup"><span data-stu-id="6a8bf-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="6a8bf-109">**✓ CONSIDER** se terminant par le nom de classes dérivées portant le nom de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="6a8bf-110">Cela est très lisible et explique clairement la relation.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="6a8bf-111">Voici quelques exemples de ceci dans le code : `ArgumentOutOfRangeException`, qui est un type de `Exception`et `SerializableAttribute`, qui est un type de `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="6a8bf-112">Toutefois, il est important d’utiliser un jugement raisonnable dans le cadre de l’application de cette règle. par exemple, la classe `Button` est un genre d’événement `Control`, bien que `Control` n’apparaisse pas dans son nom.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="6a8bf-113">**✓ DO** préfixe les noms d’interface avec la lettre I, pour indiquer que le type est une interface.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="6a8bf-114">Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression nominale) et `IPersistable` (adjectif) sont des noms d’interface appropriés.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="6a8bf-115">Comme avec d’autres noms de types, évitez les abréviations.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="6a8bf-116">**✓ DO** vous assurer que les noms diffèrent uniquement par « I » du préfixe du nom de l’interface lorsque vous définissez une paire : interface de classe dans laquelle la classe est une implémentation standard de l’interface.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="6a8bf-117">Noms des paramètres de type générique</span><span class="sxs-lookup"><span data-stu-id="6a8bf-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="6a8bf-118">Des génériques ont été ajoutés à .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="6a8bf-119">La fonctionnalité a introduit un nouveau type d’identificateur appelé *paramètre de type*.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="6a8bf-120">**✓ DO** nom des paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est complètement explicite et un nom descriptif ajouterait pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="6a8bf-121">**✓ CONSIDER** à l’aide de `T` comme nom de paramètre de type pour les types avec un paramètre de type de lettre unique.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="6a8bf-122">**✓ DO** préfixe des noms de paramètre de type descriptifs avec `T`.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="6a8bf-123">**✓ CONSIDER** indiquer les contraintes placées sur un paramètre de type dans le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="6a8bf-124">Par exemple, un paramètre restreint à `ISession` peut être appelé `TSession`.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="6a8bf-125">Noms des types courants</span><span class="sxs-lookup"><span data-stu-id="6a8bf-125">Names of Common Types</span></span>  
 <span data-ttu-id="6a8bf-126">**✓ DO** suivez les instructions décrites dans le tableau suivant lorsque vous nommez des types dérivés ou implémenter certains types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="6a8bf-127">Base Type</span><span class="sxs-lookup"><span data-stu-id="6a8bf-127">Base Type</span></span>|<span data-ttu-id="6a8bf-128">Instruction de type Derived/Implementation</span><span class="sxs-lookup"><span data-stu-id="6a8bf-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="6a8bf-129">**✓ DO** ajouter le suffixe « Attribute » aux noms des classes d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="6a8bf-130">**✓ DO** ajouter le suffixe « EventHandler » aux noms de délégués qui sont utilisés dans les événements.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="6a8bf-131">**✓ DO** ajouter le suffixe « Rappel » aux noms de délégués autres que ceux utilisés en tant que gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="6a8bf-132">**X DO NOT** ajouter le suffixe « Délégué » à un délégué.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="6a8bf-133">**✓ DO** ajouter le suffixe « EventArgs ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="6a8bf-134">**X DO NOT** dériver de cette classe ; utilisez le mot clé pris en charge par votre langage à la place ; par exemple, en c#, utilisez le `enum` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="6a8bf-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="6a8bf-135">**X DO NOT** ajouter le suffixe « Enum » ou « Indicateur ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="6a8bf-136">**✓ DO** ajouter le suffixe « Exception ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="6a8bf-137">**✓ DO** ajouter le suffixe « Dictionnaire ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="6a8bf-138">Notez que `IDictionary` est un type de collection spécifique, mais cette règle est prioritaire sur la règle de regroupements plus généraux qui suit.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="6a8bf-139">**✓ DO** ajouter le suffixe « Collection ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="6a8bf-140">**✓ DO** ajouter le suffixe « Stream ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="6a8bf-141">**✓ DO** ajouter le suffixe « Autorisation ».</span><span class="sxs-lookup"><span data-stu-id="6a8bf-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="6a8bf-142">Énumération des noms</span><span class="sxs-lookup"><span data-stu-id="6a8bf-142">Naming Enumerations</span></span>  
 <span data-ttu-id="6a8bf-143">En général, les noms de types énumération (également appelés énumérations) doivent respecter les règles d’attribution de noms de type standard (PascalCasing, etc.).</span><span class="sxs-lookup"><span data-stu-id="6a8bf-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="6a8bf-144">Toutefois, des instructions supplémentaires s’appliquent spécifiquement aux enums.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="6a8bf-145">**✓ DO** utiliser un nom de type au singulier pour une énumération, sauf si ses valeurs sont les champs de bits.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="6a8bf-146">**✓ DO** utiliser un nom de type au pluriel pour une énumération avec les champs de bits sous forme de valeurs, également appelés enum d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="6a8bf-147">**X DO NOT** utiliser le suffixe « Enum » dans les noms de type enum.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="6a8bf-148">**X DO NOT** utiliser « Indicateur » ou tapez les noms des suffixes « Indicateurs » dans l’enum.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="6a8bf-149">**X DO NOT** utiliser un préfixe sur les noms de valeur d’énumération (par exemple, « ad » pour les énumérations ADO.), « rtf » pour les énumérations de texte enrichi, etc.</span><span class="sxs-lookup"><span data-stu-id="6a8bf-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="6a8bf-150">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6a8bf-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a8bf-151">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a8bf-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8bf-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a8bf-152">See also</span></span>

- [<span data-ttu-id="6a8bf-153">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a8bf-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6a8bf-154">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="6a8bf-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
