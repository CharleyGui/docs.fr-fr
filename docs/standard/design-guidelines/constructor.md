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
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400602"
---
# <a name="constructor-design"></a><span data-ttu-id="98113-102">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="98113-102">Constructor Design</span></span>

<span data-ttu-id="98113-103">Il existe deux types de constructeurs : les constructeurs de type et les constructeurs d’instance.</span><span class="sxs-lookup"><span data-stu-id="98113-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="98113-104">Les constructeurs de type sont statiques et sont gérés par le CLR avant que le type ne soit utilisé.</span><span class="sxs-lookup"><span data-stu-id="98113-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="98113-105">Les constructeurs d’instance s’exécutent lorsqu’une instance d’un type est créée.</span><span class="sxs-lookup"><span data-stu-id="98113-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="98113-106">Les constructeurs de type ne peuvent pas prendre de paramètres.</span><span class="sxs-lookup"><span data-stu-id="98113-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="98113-107">Les constructeurs d’instance peuvent.</span><span class="sxs-lookup"><span data-stu-id="98113-107">Instance constructors can.</span></span> <span data-ttu-id="98113-108">Les constructeurs d’instance qui ne prennent aucun paramètre sont souvent appelés constructeurs sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="98113-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="98113-109">Les constructeurs sont le moyen le plus naturel de créer des instances de type.</span><span class="sxs-lookup"><span data-stu-id="98113-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="98113-110">La plupart des développeurs vont rechercher et essayer d’utiliser un constructeur avant d’envisager d’autres moyens de créer des instances (telles que les méthodes d’usine).</span><span class="sxs-lookup"><span data-stu-id="98113-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="98113-111">✔️ CONSIDER fournissant des constructeurs simples, idéalement par défaut.</span><span class="sxs-lookup"><span data-stu-id="98113-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="98113-112">Un constructeur simple a un très petit nombre de paramètres, et tous les paramètres sont primitifs ou enums.</span><span class="sxs-lookup"><span data-stu-id="98113-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="98113-113">Ces constructeurs simples augmentent la convivialité du cadre.</span><span class="sxs-lookup"><span data-stu-id="98113-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="98113-114">✔️ CONSIDER en utilisant une méthode d’usine statique au lieu d’un constructeur si la sémantique de l’opération désirée ne cartographie pas directement à la construction d’une nouvelle instance, ou si suivre les directives de conception du constructeur se sent contre nature.</span><span class="sxs-lookup"><span data-stu-id="98113-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="98113-115">✔️ UTILISEZ les paramètres du constructeur comme raccourcis pour définir les propriétés principales.</span><span class="sxs-lookup"><span data-stu-id="98113-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="98113-116">Il ne devrait y avoir aucune différence dans la sémantique entre l’utilisation du constructeur vide suivi par certains ensembles de propriété et l’utilisation d’un constructeur avec de multiples arguments.</span><span class="sxs-lookup"><span data-stu-id="98113-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="98113-117">✔️ NE pas utiliser le même nom pour les paramètres constructeur et une propriété si les paramètres du constructeur sont utilisés pour simplement définir la propriété.</span><span class="sxs-lookup"><span data-stu-id="98113-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="98113-118">La seule différence entre ces paramètres et les propriétés doit être le boîtier.</span><span class="sxs-lookup"><span data-stu-id="98113-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="98113-119">✔️ FAITES un travail minimal dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="98113-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="98113-120">Les constructeurs ne doivent pas faire beaucoup de travail autre que la capture des paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="98113-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="98113-121">Le coût de tout autre traitement doit être retardé jusqu’à ce qu’il soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="98113-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="98113-122">✔️ NE jeter des exceptions de constructeurs d’instance, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="98113-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="98113-123">✔️ NE déclarez explicitement le constructeur public sans paramètres dans les classes, si un tel constructeur est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="98113-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="98113-124">Si vous ne déclarez pas explicitement les constructeurs sur un type, de nombreuses langues (comme le C) ajouteront automatiquement un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="98113-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="98113-125">(Les classes abstraites obtiennent un constructeur protégé.)</span><span class="sxs-lookup"><span data-stu-id="98113-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="98113-126">L’ajout d’un constructeur paramétré à une classe empêche le compilateur d’ajouter le constructeur sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="98113-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="98113-127">Cela provoque souvent des changements de rupture accidentelle.</span><span class="sxs-lookup"><span data-stu-id="98113-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="98113-128">❌AVOID définissant explicitement les constructeurs sans paramètres sur les structs.</span><span class="sxs-lookup"><span data-stu-id="98113-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="98113-129">Cela rend la création de tableau plus rapide, parce que si le constructeur sans paramètres n’est pas défini, il n’a pas à être exécuté sur chaque fente dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="98113-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="98113-130">Notez que de nombreux compilateurs, y compris le C, ne permettent pas aux structs d’avoir des constructeurs sans paramètres pour cette raison.</span><span class="sxs-lookup"><span data-stu-id="98113-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="98113-131">❌AVOID appelant des membres virtuels sur un objet à l’intérieur de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="98113-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="98113-132">L’appel d’un membre virtuel entraînera l’appel du remplacement le plus dérivé, même si le constructeur du type le plus dérivé n’a pas encore été entièrement exécuté.</span><span class="sxs-lookup"><span data-stu-id="98113-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="98113-133">Lignes directrices sur les constructeurs de types</span><span class="sxs-lookup"><span data-stu-id="98113-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="98113-134">✔️ NE rendre les constructeurs statiques privés.</span><span class="sxs-lookup"><span data-stu-id="98113-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="98113-135">Un constructeur statique, également appelé un constructeur de classe, est utilisé pour initialiser un type.</span><span class="sxs-lookup"><span data-stu-id="98113-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="98113-136">Le CLR appelle le constructeur statique avant la création de la première instance du type ou que des membres statiques de ce type soient appelés.</span><span class="sxs-lookup"><span data-stu-id="98113-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="98113-137">L’utilisateur n’a aucun contrôle sur quand le constructeur statique est appelé.</span><span class="sxs-lookup"><span data-stu-id="98113-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="98113-138">Si un constructeur statique n’est pas privé, il peut être appelé par code autre que le CLR.</span><span class="sxs-lookup"><span data-stu-id="98113-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="98113-139">Selon les opérations effectuées dans le constructeur, cela peut causer un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="98113-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="98113-140">Le compilateur CMD force les constructeurs statiques à être privés.</span><span class="sxs-lookup"><span data-stu-id="98113-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="98113-141">❌NE PAS jeter des exceptions des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="98113-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="98113-142">Si une exception est projetée à partir d’un constructeur type, le type n’est pas utilisable dans le domaine actuel de l’application.</span><span class="sxs-lookup"><span data-stu-id="98113-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="98113-143">✔️ CONSIDER initialisant les champs statiques en ligne plutôt que d’utiliser explicitement des constructeurs statiques, parce que le temps d’exécution est capable d’optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.</span><span class="sxs-lookup"><span data-stu-id="98113-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="98113-144">*Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="98113-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="98113-145">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="98113-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="98113-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98113-146">See also</span></span>

- [<span data-ttu-id="98113-147">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="98113-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="98113-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98113-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
