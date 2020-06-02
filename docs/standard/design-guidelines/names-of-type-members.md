---
title: Noms de membres de type
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 87cf793229cfc7d8d0547af935369a3febee41a3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290186"
---
# <a name="names-of-type-members"></a><span data-ttu-id="319a3-102">Noms de membres de type</span><span class="sxs-lookup"><span data-stu-id="319a3-102">Names of Type Members</span></span>
<span data-ttu-id="319a3-103">Les types se composent de membres, de méthodes, de propriétés, d’événements, de constructeurs et de champs.</span><span class="sxs-lookup"><span data-stu-id="319a3-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="319a3-104">Les sections suivantes décrivent les règles de nommage des membres de type.</span><span class="sxs-lookup"><span data-stu-id="319a3-104">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="319a3-105">Noms des méthodes</span><span class="sxs-lookup"><span data-stu-id="319a3-105">Names of Methods</span></span>
 <span data-ttu-id="319a3-106">Comme les méthodes permettent d’entreprendre des actions, les règles de conception exigent que les noms des méthodes soient des verbes ou des expressions verbales.</span><span class="sxs-lookup"><span data-stu-id="319a3-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="319a3-107">Cette règle sert également à distinguer les noms de méthode des noms de propriété et de type, qui sont des expressions nominales ou adjectivales.</span><span class="sxs-lookup"><span data-stu-id="319a3-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="319a3-108">✔️ Donnez des noms de méthodes qui sont des verbes ou des expressions de verbe.</span><span class="sxs-lookup"><span data-stu-id="319a3-108">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="319a3-109">Noms des propriétés</span><span class="sxs-lookup"><span data-stu-id="319a3-109">Names of Properties</span></span>
 <span data-ttu-id="319a3-110">Contrairement aux autres membres, les noms des propriétés doivent être des expressions nominales ou adjectivales.</span><span class="sxs-lookup"><span data-stu-id="319a3-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="319a3-111">C’est parce que les propriétés font référence à des données, donc leur nom doivent le refléter.</span><span class="sxs-lookup"><span data-stu-id="319a3-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="319a3-112">La casse Pascal est toujours utilisée pour les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="319a3-112">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="319a3-113">✔️ Nommez les propriétés à l’aide d’un nom, d’une expression nominale ou d’un adjectif.</span><span class="sxs-lookup"><span data-stu-id="319a3-113">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="319a3-114">❌N’avez pas de propriétés qui correspondent au nom des méthodes « obtenir » comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="319a3-114">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="319a3-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="319a3-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="319a3-116">Ce modèle indique typiquement que la propriété doit vraiment être une méthode.</span><span class="sxs-lookup"><span data-stu-id="319a3-116">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="319a3-117">✔️ Nommez les propriétés de collection avec une expression pluriel décrivant les éléments de la collection au lieu d’utiliser une expression singulière suivie de « List » ou « collection ».</span><span class="sxs-lookup"><span data-stu-id="319a3-117">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="319a3-118">✔️ Nommez les propriétés booléennes avec une expression affirmative ( `CanSeek` au lieu de `CantSeek` ).</span><span class="sxs-lookup"><span data-stu-id="319a3-118">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="319a3-119">Si vous le souhaitez, vous pouvez également préfixer les propriétés booléennes avec « is », « CAN » ou « has », mais uniquement à l’endroit où elle ajoute value.</span><span class="sxs-lookup"><span data-stu-id="319a3-119">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="319a3-120">✔️ envisagez de donner à une propriété le même nom que son type.</span><span class="sxs-lookup"><span data-stu-id="319a3-120">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="319a3-121">Par exemple, la propriété suivante obtient et définit correctement une valeur enum nommée `Color`, donc la propriété est nommée `Color`:</span><span class="sxs-lookup"><span data-stu-id="319a3-121">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="319a3-122">Noms des événements</span><span class="sxs-lookup"><span data-stu-id="319a3-122">Names of Events</span></span>
 <span data-ttu-id="319a3-123">Les événements font toujours référence à une action, soit une action en cours, soit une action passée.</span><span class="sxs-lookup"><span data-stu-id="319a3-123">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="319a3-124">Par conséquent, comme avec les méthodes, les événements sont nommés avec des verbes, le temps des verbes servant à indiquer l’heure où l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="319a3-124">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="319a3-125">✔️ Nommez les événements avec un verbe ou une phrase verbale.</span><span class="sxs-lookup"><span data-stu-id="319a3-125">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="319a3-126">Par exemple, `Clicked`, `Painting`, `DroppedDown`, etc.</span><span class="sxs-lookup"><span data-stu-id="319a3-126">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="319a3-127">✔️ Donnez des noms d’événements avec un concept antérieur et postérieur, en utilisant les dizaines présents et précédents.</span><span class="sxs-lookup"><span data-stu-id="319a3-127">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="319a3-128">Par exemple, un événement de fermeture déclenché avant la fermeture d’une fenêtre serait nommé `Closing`, tandis qu’un événement déclenché après la fermeture de la fenêtre serait nommé `Closed`.</span><span class="sxs-lookup"><span data-stu-id="319a3-128">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="319a3-129">❌N’utilisez pas les préfixes ou les suffixes « Before » ou « after » pour indiquer les pré-et post-événements.</span><span class="sxs-lookup"><span data-stu-id="319a3-129">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="319a3-130">Utilisez les temps du présent et du passé, comme nous venons de le décrire.</span><span class="sxs-lookup"><span data-stu-id="319a3-130">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="319a3-131">✔️ Nommez les gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="319a3-131">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="319a3-132">✔️ Utilisez deux paramètres nommés `sender` et `e` dans des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="319a3-132">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="319a3-133">Le paramètre d’expéditeur représente l’objet qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="319a3-133">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="319a3-134">Le paramètre d’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="319a3-134">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="319a3-135">✔️ Nommez les classes d’argument d’événement avec le suffixe « EventArgs ».</span><span class="sxs-lookup"><span data-stu-id="319a3-135">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="319a3-136">Noms des champs</span><span class="sxs-lookup"><span data-stu-id="319a3-136">Names of Fields</span></span>
 <span data-ttu-id="319a3-137">Les règles de nommage des champs s’appliquent à des champs publics et protégés statiques.</span><span class="sxs-lookup"><span data-stu-id="319a3-137">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="319a3-138">Les champs internes et privés ne sont pas couverts par les règles, tandis que les champs d’instance publics ou protégés ne sont pas autorisés par les [règles de conception de membres](member.md).</span><span class="sxs-lookup"><span data-stu-id="319a3-138">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="319a3-139">✔️ Utilisez PascalCasing dans les noms de champs.</span><span class="sxs-lookup"><span data-stu-id="319a3-139">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="319a3-140">✔️ Nommez les champs à l’aide d’un nom, d’une expression nominale ou d’un adjectif.</span><span class="sxs-lookup"><span data-stu-id="319a3-140">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="319a3-141">❌N’utilisez pas de préfixe pour les noms de champs.</span><span class="sxs-lookup"><span data-stu-id="319a3-141">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="319a3-142">Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer des champs statiques.</span><span class="sxs-lookup"><span data-stu-id="319a3-142">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="319a3-143">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="319a3-143">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="319a3-144">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="319a3-144">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="319a3-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="319a3-145">See also</span></span>

- [<span data-ttu-id="319a3-146">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="319a3-146">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="319a3-147">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="319a3-147">Naming Guidelines</span></span>](naming-guidelines.md)
