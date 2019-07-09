---
title: Conception d'énumérations
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: e890ebbbeb04ca424b84c11791e5ce7fa55db72e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663480"
---
# <a name="enum-design"></a><span data-ttu-id="6a45b-102">Conception d'énumérations</span><span class="sxs-lookup"><span data-stu-id="6a45b-102">Enum Design</span></span>

<span data-ttu-id="6a45b-103">Les enums sont un type spécial de type valeur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="6a45b-104">Il existe deux types d’énumérations : les enums enums et indicateur simples.</span><span class="sxs-lookup"><span data-stu-id="6a45b-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="6a45b-105">Énumérations simples représentent des petits ensembles fermés de choix.</span><span class="sxs-lookup"><span data-stu-id="6a45b-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="6a45b-106">Un exemple courant de l’enum simple est un jeu de couleurs.</span><span class="sxs-lookup"><span data-stu-id="6a45b-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="6a45b-107">Énumérations d’indicateur sont conçues pour prendre en charge des opérations au niveau du bit sur les valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="6a45b-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="6a45b-108">Un exemple courant de l’énumération d’indicateurs est une liste d’options.</span><span class="sxs-lookup"><span data-stu-id="6a45b-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="6a45b-109">**✓ DO** permet un enum de type fort aux paramètres, propriétés et retourner des valeurs qui représentent les ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6a45b-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="6a45b-110">**✓ DO** sont favorables à l’aide d’un enum au lieu de constantes statiques.</span><span class="sxs-lookup"><span data-stu-id="6a45b-110">**✓ DO** favor using an enum instead of static constants.</span></span>

<span data-ttu-id="6a45b-111">**X DO NOT** utiliser un enum pour les ensembles ouverts (par exemple, la version du système d’exploitation, les noms de vos amis, un etc.).</span><span class="sxs-lookup"><span data-stu-id="6a45b-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="6a45b-112">**X DO NOT** fournissent des valeurs d’enum réservé qui sont destinés à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="6a45b-113">Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un stade ultérieur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="6a45b-114">Consultez [Ajout de valeurs aux Enums](#add_value) pour plus d’informations sur l’ajout de valeurs aux enums.</span><span class="sxs-lookup"><span data-stu-id="6a45b-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="6a45b-115">Simplement les valeurs réservées polluent l’ensemble de valeurs réelles et ont tendance à provoquer des erreurs de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="6a45b-116">**X AVOID** exposer publiquement des énumérations avec une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-116">**X AVOID** publicly exposing enums with only one value.</span></span>

<span data-ttu-id="6a45b-117">Une pratique courante pour assurer une extensibilité future de l’API C consiste à ajouter des paramètres réservés aux signatures de méthode.</span><span class="sxs-lookup"><span data-stu-id="6a45b-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="6a45b-118">Ces paramètres réservés peuvent être exprimées en tant qu’énumérations avec une valeur unique par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a45b-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="6a45b-119">Cela ne doit pas être effectuée dans les API gérées.</span><span class="sxs-lookup"><span data-stu-id="6a45b-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="6a45b-120">La surcharge de méthode permet d’ajouter des paramètres dans les versions futures.</span><span class="sxs-lookup"><span data-stu-id="6a45b-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="6a45b-121">**X DO NOT** inclure des valeurs de sentinelle dans les énumérations.</span><span class="sxs-lookup"><span data-stu-id="6a45b-121">**X DO NOT** include sentinel values in enums.</span></span>

<span data-ttu-id="6a45b-122">Même s’ils sont parfois utiles aux développeurs de framework, les valeurs de sentinelle sont confus pour les utilisateurs du framework.</span><span class="sxs-lookup"><span data-stu-id="6a45b-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="6a45b-123">Ils sont utilisés pour effectuer le suivi de l’état de l’enum plutôt que d’être une des valeurs à partir de l’ensemble représenté par l’énumération.</span><span class="sxs-lookup"><span data-stu-id="6a45b-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="6a45b-124">**✓ DO** fournir une valeur de zéro sur les énumérations simples.</span><span class="sxs-lookup"><span data-stu-id="6a45b-124">**✓ DO** provide a value of zero on simple enums.</span></span>

<span data-ttu-id="6a45b-125">La valeur, appelez quelque chose comme « None ».</span><span class="sxs-lookup"><span data-stu-id="6a45b-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="6a45b-126">Si une telle valeur n’est pas appropriée pour cet enum particulier, la valeur par défaut courante pour l’énumération doit avoir la valeur sous-jacente égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="6a45b-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="6a45b-127">**✓ CONSIDER** à l’aide de <xref:System.Int32> (la valeur par défaut dans la plupart des langages de programmation) en tant que le type sous-jacent d’une énumération, sauf si une des opérations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="6a45b-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="6a45b-128">L’énumération est une énumération d’indicateurs, et vous disposez de plus de 32 indicateurs ou souhaitez avoir plus d’informations à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="6a45b-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="6a45b-129">Le type sous-jacent doit être différent de celui <xref:System.Int32> pour simplifier l’interopérabilité avec le code non managé attendu des énumérations de taille différente.</span><span class="sxs-lookup"><span data-stu-id="6a45b-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="6a45b-130">Un type sous-jacent plus petit entraînerait des économies substantielles dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="6a45b-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="6a45b-131">Si vous pensez que l’énumération à utiliser principalement en tant qu’argument pour le flux de contrôle, la taille importe peu.</span><span class="sxs-lookup"><span data-stu-id="6a45b-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="6a45b-132">Les économies de taille peuvent être importantes si :</span><span class="sxs-lookup"><span data-stu-id="6a45b-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="6a45b-133">Vous pensez que l’énumération à utiliser en tant que champ dans une structure très fréquemment instanciée ou une classe.</span><span class="sxs-lookup"><span data-stu-id="6a45b-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="6a45b-134">Vous prévoyez que les utilisateurs à créer des grands tableaux ou collections d’instances de l’enum.</span><span class="sxs-lookup"><span data-stu-id="6a45b-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="6a45b-135">Vous prévoyez un grand nombre d’instances de l’énumération à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="6a45b-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="6a45b-136">Pour une utilisation en mémoire, n’oubliez pas que les objets managés sont toujours `DWORD`-alignés, vous devez efficacement plusieurs énumérations ou autres petites structures dans une instance de compresser un enum plus petits avec afin de faire la différence, car la taille du nombre total d’instances est toujours sera arrondie à un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6a45b-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="6a45b-137">**✓ DO** nommer les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et énumérations simples avec des noms au singulier ou des expressions nominales.</span><span class="sxs-lookup"><span data-stu-id="6a45b-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="6a45b-138">**X DO NOT** étendre <xref:System.Enum?displayProperty=nameWithType> directement.</span><span class="sxs-lookup"><span data-stu-id="6a45b-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="6a45b-139"><xref:System.Enum?displayProperty=nameWithType> est un type spécial utilisé par le CLR pour créer des énumérations définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="6a45b-140">La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="6a45b-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="6a45b-141">Par exemple, en c# le `enum` mot clé est utilisé pour définir une énumération.</span><span class="sxs-lookup"><span data-stu-id="6a45b-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="6a45b-142">Conception énumérations d’indicateur</span><span class="sxs-lookup"><span data-stu-id="6a45b-142">Designing Flag Enums</span></span>

<span data-ttu-id="6a45b-143">**✓ DO** appliquer le <xref:System.FlagsAttribute?displayProperty=nameWithType> pour les énumérations d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="6a45b-144">N’appliquez pas cet attribut aux enums simples.</span><span class="sxs-lookup"><span data-stu-id="6a45b-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="6a45b-145">**✓ DO** utiliser des puissances de deux pour les valeurs d’énumération indicateur afin qu’ils peuvent être combinés librement à l’aide de l’opération OR au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="6a45b-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="6a45b-146">**✓ CONSIDER** fournissant des valeurs enum spécial pour couramment utilisé les combinaisons d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="6a45b-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="6a45b-147">Opérations de bits sont un concept avancé et ne doivent pas être requises pour des tâches simples.</span><span class="sxs-lookup"><span data-stu-id="6a45b-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="6a45b-148"><xref:System.IO.FileAccess.ReadWrite> est un exemple d’une telle valeur spéciale.</span><span class="sxs-lookup"><span data-stu-id="6a45b-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="6a45b-149">**X AVOID** création enums indicateur où certaines combinaisons de valeurs ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="6a45b-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="6a45b-150">**X AVOID** à l’aide de valeurs de l’indicateur enum de zéro, sauf si la valeur représente « tous les indicateurs sont effacés » et est nommée de façon appropriée, comme indiqué par l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="6a45b-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="6a45b-151">**✓ DO** nom de la valeur zéro des énumérations d’indicateur `None`.</span><span class="sxs-lookup"><span data-stu-id="6a45b-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="6a45b-152">Pour une énumération d’indicateur, la valeur doit toujours signifier « tous les indicateurs sont effacés. »</span><span class="sxs-lookup"><span data-stu-id="6a45b-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="6a45b-153">Ajout de valeur aux Enums</span><span class="sxs-lookup"><span data-stu-id="6a45b-153">Adding Value to Enums</span></span>

<span data-ttu-id="6a45b-154">Il est très courant pour découvrir que vous avez besoin ajouter des valeurs à un enum une fois que vous l’avez déjà expédié.</span><span class="sxs-lookup"><span data-stu-id="6a45b-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="6a45b-155">Il est un problème de compatibilité d’application potentiel que quand la valeur nouvellement ajoutée est retournée à partir d’une API existante, car des applications mal écrites peut ne pas gérer correctement la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="6a45b-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="6a45b-156">**✓ CONSIDER** Ajout de valeurs pour les enums, en dépit d’un léger risque de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="6a45b-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="6a45b-157">Si vous avez des données réelles concernant les incompatibilités d’application a provoqué par des ajouts à un enum, envisagez d’ajouter une nouvelle API qui retourne les valeurs anciennes et nouvelles et déprécier l’ancienne API, qui doit continuer à retourner simplement les anciennes valeurs.</span><span class="sxs-lookup"><span data-stu-id="6a45b-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="6a45b-158">Cela garantit que vos applications existantes restent compatibles.</span><span class="sxs-lookup"><span data-stu-id="6a45b-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="6a45b-159">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6a45b-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="6a45b-160">*Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a45b-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6a45b-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a45b-161">See also</span></span>

- [<span data-ttu-id="6a45b-162">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="6a45b-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="6a45b-163">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a45b-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
