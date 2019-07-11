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
author: KrzysztofCwalina
ms.openlocfilehash: 074aa391b71257584a01171e95da7472354cdc2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746780"
---
# <a name="constructor-design"></a><span data-ttu-id="fafce-102">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="fafce-102">Constructor Design</span></span>
<span data-ttu-id="fafce-103">Il existe deux types de constructeurs : tapez des constructeurs et des constructeurs d’instance.</span><span class="sxs-lookup"><span data-stu-id="fafce-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="fafce-104">Constructeurs de type sont statiques et sont exécutés par le CLR avant que le type est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fafce-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="fafce-105">Constructeurs d’instance exécuté lorsqu’une instance d’un type est créée.</span><span class="sxs-lookup"><span data-stu-id="fafce-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="fafce-106">Constructeurs de type ne peut pas prendre tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="fafce-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="fafce-107">Constructeurs d’instance peuvent.</span><span class="sxs-lookup"><span data-stu-id="fafce-107">Instance constructors can.</span></span> <span data-ttu-id="fafce-108">Constructeurs d’instance qui ne prennent pas tous les paramètres sont souvent appelées des constructeurs sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="fafce-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>  
  
 <span data-ttu-id="fafce-109">Constructeurs sont le moyen le plus naturel pour créer des instances d’un type.</span><span class="sxs-lookup"><span data-stu-id="fafce-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="fafce-110">La plupart des développeurs recherche et essayez d’utiliser un constructeur avant d’autres méthodes de création d’instances (par exemple, les méthodes de fabrique).</span><span class="sxs-lookup"><span data-stu-id="fafce-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="fafce-111">**✓ CONSIDER** fournissant simple, dans l’idéal, par défaut, les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="fafce-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="fafce-112">Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou des énumérations.</span><span class="sxs-lookup"><span data-stu-id="fafce-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="fafce-113">Ces constructeurs simples faciliter l’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="fafce-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="fafce-114">**✓ CONSIDER** à l’aide d’une méthode de fabrique statique au lieu d’un constructeur si la sémantique de l’opération requise ne correspond pas directement à la construction d’une nouvelle instance, ou si les règles de conception du constructeur vous semblent pas naturelles.</span><span class="sxs-lookup"><span data-stu-id="fafce-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="fafce-115">**✓ DO** utiliser les paramètres du constructeur en tant que raccourcis pour définir les propriétés principales.</span><span class="sxs-lookup"><span data-stu-id="fafce-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="fafce-116">Il doit y avoir aucune différence sémantique entre l’utilisation du constructeur vide suivi de certains jeux de propriétés et à l’aide d’un constructeur avec plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="fafce-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="fafce-117">**✓ DO** utiliser le même nom pour les paramètres du constructeur et une propriété si les paramètres du constructeur sont utilisés pour définir simplement la propriété.</span><span class="sxs-lookup"><span data-stu-id="fafce-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="fafce-118">Doit être la seule différence entre ces paramètres et les propriétés de mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="fafce-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="fafce-119">**✓ DO** travail minimal dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="fafce-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="fafce-120">Constructeurs doivent rien faire d’autre que de capture les paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="fafce-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="fafce-121">Le coût de tout autre traitement doit être différé jusqu'à ce que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fafce-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="fafce-122">**✓ DO** lever des exceptions à partir des constructeurs d’instance, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="fafce-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="fafce-123">**FAIRE ✓** déclarer explicitement le constructeur sans paramètre public dans les classes, si ce constructeur est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fafce-123">**✓ DO** explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="fafce-124">Si vous ne déclarez explicitement les constructeurs sur un type, de nombreux langages (tels que C#) ajoute automatiquement un constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="fafce-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="fafce-125">(Les classes abstraites obtenir un constructeur protégé.)</span><span class="sxs-lookup"><span data-stu-id="fafce-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="fafce-126">Ajout d’un constructeur paramétrable à une classe empêche le compilateur d’ajouter le constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="fafce-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="fafce-127">Cela entraîne souvent des modifications avec rupture accidentelle.</span><span class="sxs-lookup"><span data-stu-id="fafce-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="fafce-128">**X Évitez** définition explicite des constructeurs sans paramètre sur les structures.</span><span class="sxs-lookup"><span data-stu-id="fafce-128">**X AVOID** explicitly defining parameterless constructors on structs.</span></span>  
  
 <span data-ttu-id="fafce-129">Cela accélère la création de tableau, car si le constructeur sans paramètre n’est pas défini, il n’a pas à être exécuté sur tous les emplacements dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="fafce-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="fafce-130">Notez que de nombreux compilateurs, y compris C#, ne pas autoriser les structs peuvent avoir des constructeurs sans paramètre pour cette raison.</span><span class="sxs-lookup"><span data-stu-id="fafce-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="fafce-131">**X AVOID** appel des membres virtuels sur un objet à l’intérieur de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="fafce-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="fafce-132">Appeler un membre virtuel entraîne le remplacement de la plus dérivé à appeler, même si le constructeur du type plus dérivé n'a pas été entièrement encore été exécuté.</span><span class="sxs-lookup"><span data-stu-id="fafce-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="fafce-133">Instructions de constructeur de type</span><span class="sxs-lookup"><span data-stu-id="fafce-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="fafce-134">**✓ DO** rendre les constructeurs statiques privé.</span><span class="sxs-lookup"><span data-stu-id="fafce-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="fafce-135">Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type.</span><span class="sxs-lookup"><span data-stu-id="fafce-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="fafce-136">Le CLR appelle le constructeur statique avant la création de la première instance du type ou de tous les membres statiques sur ce type sont appelées.</span><span class="sxs-lookup"><span data-stu-id="fafce-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="fafce-137">L’utilisateur n’a aucun contrôle sur quand le constructeur statique est appelé.</span><span class="sxs-lookup"><span data-stu-id="fafce-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="fafce-138">Si un constructeur statique n’est pas privé, elle peut être appelée par du code autre que le CLR.</span><span class="sxs-lookup"><span data-stu-id="fafce-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="fafce-139">Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="fafce-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="fafce-140">Le compilateur c# force les constructeurs statiques privées.</span><span class="sxs-lookup"><span data-stu-id="fafce-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="fafce-141">**X DO NOT** lever des exceptions à partir des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="fafce-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="fafce-142">Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="fafce-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="fafce-143">**✓ CONSIDER** initialiser les champs statiques inline au lieu d’utiliser explicitement des constructeurs statiques, car le runtime peut optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.</span><span class="sxs-lookup"><span data-stu-id="fafce-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="fafce-144">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="fafce-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fafce-145">*Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fafce-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafce-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fafce-146">See also</span></span>

- [<span data-ttu-id="fafce-147">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="fafce-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="fafce-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fafce-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
