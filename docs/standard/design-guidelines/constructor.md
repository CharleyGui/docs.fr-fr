---
title: Conception de constructeurs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: a258bebac57258cc1e8fbe2d6b5ccce88cb28872
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280346"
---
# <a name="constructor-design"></a><span data-ttu-id="c1bb4-102">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="c1bb4-102">Constructor Design</span></span>

<span data-ttu-id="c1bb4-103">Il existe deux genres de constructeurs : des constructeurs de type et des constructeurs d’instance.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="c1bb4-104">Les constructeurs de type sont statiques et sont exécutés par le CLR avant l’utilisation du type.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="c1bb4-105">Les constructeurs d’instance s’exécutent lors de la création d’une instance d’un type.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="c1bb4-106">Les constructeurs de type ne peuvent pas accepter de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="c1bb4-107">Les constructeurs d’instance peuvent.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-107">Instance constructors can.</span></span> <span data-ttu-id="c1bb4-108">Les constructeurs d’instance qui ne prennent pas de paramètres sont souvent appelés constructeurs sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="c1bb4-109">Les constructeurs sont le moyen le plus naturel de créer des instances d’un type.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="c1bb4-110">La plupart des développeurs recherchent et essaient d’utiliser un constructeur avant qu’ils n’envisagent d’autres façons de créer des instances (comme les méthodes de fabrique).</span><span class="sxs-lookup"><span data-stu-id="c1bb4-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="c1bb4-111">✔️ envisagez de fournir des constructeurs simples, idéalement par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="c1bb4-112">Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou des enums.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="c1bb4-113">Ces constructeurs simples augmentent l’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="c1bb4-114">✔️ envisagez d’utiliser une méthode de fabrique statique à la place d’un constructeur si la sémantique de l’opération souhaitée ne mappe pas directement à la construction d’une nouvelle instance, ou si les règles de conception de constructeur se présentent comme non naturelles.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="c1bb4-115">✔️ Utilisez des paramètres de constructeur comme raccourcis pour définir des propriétés principales.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="c1bb4-116">Il ne doit y avoir aucune différence de sémantique entre l’utilisation du constructeur vide suivi par certains jeux de propriétés et l’utilisation d’un constructeur avec plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="c1bb4-117">✔️ Utilisez le même nom pour les paramètres du constructeur et une propriété si les paramètres du constructeur sont utilisés pour définir simplement la propriété.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="c1bb4-118">La seule différence entre ces paramètres et les propriétés doit être la casse.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="c1bb4-119">✔️ EFFECTUER un travail minimal dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="c1bb4-120">Les constructeurs ne doivent pas effectuer de nombreuses tâches autres que la capture des paramètres de constructeur.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="c1bb4-121">Le coût d’un autre traitement doit être retardé jusqu’à ce qu’il soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="c1bb4-122">✔️ lever des exceptions à partir de constructeurs d’instance, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="c1bb4-123">✔️ déclarer explicitement le constructeur sans paramètre public dans les classes, si un tel constructeur est requis.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="c1bb4-124">Si vous ne déclarez pas explicitement de constructeurs sur un type, de nombreux langages (tels que C#) ajouteront automatiquement un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="c1bb4-125">(Les classes abstraites obtiennent un constructeur protégé.)</span><span class="sxs-lookup"><span data-stu-id="c1bb4-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="c1bb4-126">L’ajout d’un constructeur paramétrable à une classe empêche le compilateur d’ajouter le constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="c1bb4-127">Cela provoque souvent des modifications avec rupture accidentelles.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="c1bb4-128">❌Évitez de définir explicitement des constructeurs sans paramètre sur des structs.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="c1bb4-129">La création de tableau est ainsi plus rapide, car si le constructeur sans paramètre n’est pas défini, il n’est pas nécessaire qu’il soit exécuté sur chaque emplacement du tableau.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="c1bb4-130">Notez que de nombreux compilateurs, y compris C#, n’autorisent pas les structs à avoir des constructeurs sans paramètre pour cette raison.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="c1bb4-131">❌Évitez d’appeler des membres virtuels sur un objet à l’intérieur de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="c1bb4-132">L’appel d’un membre virtuel entraîne l’appel de la substitution la plus dérivée, même si le constructeur du type le plus dérivé n’a pas encore été complètement exécuté.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="c1bb4-133">Directives de constructeur de type</span><span class="sxs-lookup"><span data-stu-id="c1bb4-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="c1bb4-134">✔️ rendent les constructeurs statiques privés.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="c1bb4-135">Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="c1bb4-136">Le CLR appelle le constructeur statique avant la création de la première instance du type ou l’appel de tous les membres statiques de ce type.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="c1bb4-137">L’utilisateur n’a aucun contrôle sur le moment où le constructeur statique est appelé.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="c1bb4-138">Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le CLR.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="c1bb4-139">Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="c1bb4-140">Le compilateur C# force la confidentialité des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="c1bb4-141">❌NE levez pas d’exceptions à partir de constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="c1bb4-142">Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="c1bb4-143">✔️ envisagez d’initialiser des champs statiques inline plutôt que d’utiliser explicitement des constructeurs statiques, car le runtime est en mesure d’optimiser les performances des types qui n’ont pas de constructeur statique défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="c1bb4-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="c1bb4-144">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="c1bb4-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="c1bb4-145">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c1bb4-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c1bb4-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1bb4-146">See also</span></span>

- [<span data-ttu-id="c1bb4-147">Recommandations en matière de conception de membres</span><span class="sxs-lookup"><span data-stu-id="c1bb4-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="c1bb4-148">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="c1bb4-148">Framework Design Guidelines</span></span>](index.md)
