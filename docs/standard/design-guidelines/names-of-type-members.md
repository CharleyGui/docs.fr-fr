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
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353709"
---
# <a name="names-of-type-members"></a><span data-ttu-id="33dac-102">Noms de membres de type</span><span class="sxs-lookup"><span data-stu-id="33dac-102">Names of Type Members</span></span>
<span data-ttu-id="33dac-103">Les types se composent de membres, de méthodes, de propriétés, d’événements, de constructeurs et de champs.</span><span class="sxs-lookup"><span data-stu-id="33dac-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="33dac-104">Les sections suivantes décrivent les règles de nommage des membres de type.</span><span class="sxs-lookup"><span data-stu-id="33dac-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="33dac-105">Noms des méthodes</span><span class="sxs-lookup"><span data-stu-id="33dac-105">Names of Methods</span></span>  
 <span data-ttu-id="33dac-106">Comme les méthodes permettent d’entreprendre des actions, les règles de conception exigent que les noms des méthodes soient des verbes ou des expressions verbales.</span><span class="sxs-lookup"><span data-stu-id="33dac-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="33dac-107">Cette règle sert également à distinguer les noms de méthode des noms de propriété et de type, qui sont des expressions nominales ou adjectivales.</span><span class="sxs-lookup"><span data-stu-id="33dac-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="33dac-108">**✓ DO** Donner des noms de méthode qui sont des verbes ou des expressions verbales.</span><span class="sxs-lookup"><span data-stu-id="33dac-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="33dac-109">Noms des propriétés</span><span class="sxs-lookup"><span data-stu-id="33dac-109">Names of Properties</span></span>  
 <span data-ttu-id="33dac-110">Contrairement aux autres membres, les noms des propriétés doivent être des expressions nominales ou adjectivales.</span><span class="sxs-lookup"><span data-stu-id="33dac-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="33dac-111">C’est parce que les propriétés font référence à des données, donc leur nom doivent le refléter.</span><span class="sxs-lookup"><span data-stu-id="33dac-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="33dac-112">La casse Pascal est toujours utilisée pour les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="33dac-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="33dac-113">**✓ DO** Nommer les propriétés en utilisant un substantif, une expression nominale ou un adjectif.</span><span class="sxs-lookup"><span data-stu-id="33dac-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="33dac-114">**X DO NOT** Avoir des propriétés qui correspondent au nom des méthodes "Get", comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="33dac-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="33dac-115">Ce modèle indique typiquement que la propriété doit vraiment être une méthode.</span><span class="sxs-lookup"><span data-stu-id="33dac-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="33dac-116">**✓ DO** Nommer les propriétés de collection avec une expression au pluriel décrivant les éléments de la collection au lieu d’utiliser une expression au singulier suivie de « Liste » ou « Collection ».</span><span class="sxs-lookup"><span data-stu-id="33dac-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="33dac-117">**✓ DO** Nommer des propriétés booléennes avec une expression affirmative (`CanSeek` au lieu de `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="33dac-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="33dac-118">Si vous le souhaitez, vous pouvez aussi préfixer les propriétés booléennes avec « Is », « Can » ou « Has », mais uniquement si cela apporte une valeur ajoutée.</span><span class="sxs-lookup"><span data-stu-id="33dac-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="33dac-119">**✓ CONSIDER** Donner à une propriété le même nom que son type.</span><span class="sxs-lookup"><span data-stu-id="33dac-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="33dac-120">Par exemple, la propriété suivante obtient et définit correctement une valeur enum nommée `Color`, donc la propriété est nommée `Color`:</span><span class="sxs-lookup"><span data-stu-id="33dac-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="33dac-121">Noms des événements</span><span class="sxs-lookup"><span data-stu-id="33dac-121">Names of Events</span></span>  
 <span data-ttu-id="33dac-122">Les événements font toujours référence à une action, soit une action en cours, soit une action passée.</span><span class="sxs-lookup"><span data-stu-id="33dac-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="33dac-123">Par conséquent, comme avec les méthodes, les événements sont nommés avec des verbes, le temps des verbes servant à indiquer l’heure où l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="33dac-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="33dac-124">**✓ DO** Nommer les événements avec un verbe ou une expression verbale.</span><span class="sxs-lookup"><span data-stu-id="33dac-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="33dac-125">Par exemple, `Clicked`, `Painting`, `DroppedDown`, etc.</span><span class="sxs-lookup"><span data-stu-id="33dac-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="33dac-126">**✓ DO** Donner des noms d’événement avec un concept avant/après, en utilisant les temps du présent et du passé.</span><span class="sxs-lookup"><span data-stu-id="33dac-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="33dac-127">Par exemple, un événement de fermeture déclenché avant la fermeture d’une fenêtre serait nommé `Closing`, tandis qu’un événement déclenché après la fermeture de la fenêtre serait nommé `Closed`.</span><span class="sxs-lookup"><span data-stu-id="33dac-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="33dac-128">**X DO NOT** Utiliser « Before » ou « After » comme préfixes ou suffixes pour indiquer des pré/post-événements.</span><span class="sxs-lookup"><span data-stu-id="33dac-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="33dac-129">Utilisez les temps du présent et du passé, comme nous venons de le décrire.</span><span class="sxs-lookup"><span data-stu-id="33dac-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="33dac-130">**✓ DO** Nommer les gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="33dac-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="33dac-131">**✓ DO** Utiliser deux paramètres nommés `sender` et `e` dans les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="33dac-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="33dac-132">Le paramètre d’expéditeur représente l’objet qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="33dac-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="33dac-133">Le paramètre d’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="33dac-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="33dac-134">**✓ DO** Nommer les classes d’argument d’événement avec le suffixe « EventArgs ».</span><span class="sxs-lookup"><span data-stu-id="33dac-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="33dac-135">Noms des champs</span><span class="sxs-lookup"><span data-stu-id="33dac-135">Names of Fields</span></span>  
 <span data-ttu-id="33dac-136">Les règles de nommage des champs s’appliquent à des champs publics et protégés statiques.</span><span class="sxs-lookup"><span data-stu-id="33dac-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="33dac-137">Les champs internes et privés ne sont pas couverts par les règles, tandis que les champs d’instance publics ou protégés ne sont pas autorisés par les [règles de conception de membres](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="33dac-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="33dac-138">**✓ DO** Utiliser la casse Pascal dans les noms de champ.</span><span class="sxs-lookup"><span data-stu-id="33dac-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="33dac-139">**✓ DO** Nommer les champs en utilisant un substantif, une expression nominale ou un adjectif.</span><span class="sxs-lookup"><span data-stu-id="33dac-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="33dac-140">**X DO NOT** Utiliser un préfixe pour les noms de champ.</span><span class="sxs-lookup"><span data-stu-id="33dac-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="33dac-141">Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer des champs statiques.</span><span class="sxs-lookup"><span data-stu-id="33dac-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="33dac-142">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="33dac-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="33dac-143">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="33dac-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33dac-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33dac-144">See also</span></span>

- [<span data-ttu-id="33dac-145">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="33dac-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="33dac-146">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="33dac-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
