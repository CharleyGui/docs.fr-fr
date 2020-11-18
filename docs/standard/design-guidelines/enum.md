---
title: Conception d'énumérations
description: Conception pour les enums, qui sont un genre spécial de type valeur. Les énumérations simples contiennent de petits ensembles de choix fermés. Les énumérations d’indicateur prennent en charge les opérations au niveau du bit sur les valeurs enum.
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821357"
---
# <a name="enum-design"></a><span data-ttu-id="7bb4d-105">Conception d'énumérations</span><span class="sxs-lookup"><span data-stu-id="7bb4d-105">Enum Design</span></span>

<span data-ttu-id="7bb4d-106">Les enums sont un genre spécial de type valeur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="7bb4d-107">Il existe deux types d’énumérations : les énumérations simples et les énumérations d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="7bb4d-108">Les énumérations simples représentent de petits jeux de choix fermés.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="7bb4d-109">Un ensemble de couleurs est un exemple courant de l’énumération simple.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="7bb4d-110">Les enums d’indicateur sont conçus pour prendre en charge des opérations au niveau du bit sur les valeurs enum.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="7bb4d-111">Une liste d’options est un exemple courant de l’énumération Flags.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="7bb4d-112">✔️ Utilisez une énumération pour fortement taper des paramètres, des propriétés et des valeurs de retour qui représentent des ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="7bb4d-113">✔️ préférez l’utilisation d’une énumération plutôt que de constantes statiques.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="7bb4d-114">❌ N’utilisez pas d’énumération pour les jeux ouverts (tels que la version du système d’exploitation, les noms de vos amis, etc.).</span><span class="sxs-lookup"><span data-stu-id="7bb4d-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="7bb4d-115">❌ NE fournissez pas de valeurs enum réservées destinées à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="7bb4d-116">Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un moment ultérieur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="7bb4d-117">Pour plus d’informations sur l’ajout de valeurs aux enums, consultez [Ajout de valeurs aux enums](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="7bb4d-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="7bb4d-118">Les valeurs réservées polluent simplement l’ensemble des valeurs réelles et ont tendance à entraîner des erreurs de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="7bb4d-119">❌ Évitez d’exposer publiquement des enums avec une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="7bb4d-120">Une pratique courante pour garantir une extensibilité future des API C consiste à ajouter des paramètres réservés aux signatures de méthode.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="7bb4d-121">Ces paramètres réservés peuvent être exprimés comme des enums avec une seule valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="7bb4d-122">Cela ne doit pas être fait dans les API managées.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="7bb4d-123">La surcharge de méthode permet d’ajouter des paramètres dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="7bb4d-124">❌ N’incluez pas de valeurs Sentinel dans les enums.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="7bb4d-125">Bien qu’elles soient parfois utiles pour les développeurs d’infrastructure, les valeurs sentinelles sont confuses pour les utilisateurs de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="7bb4d-126">Ils sont utilisés pour suivre l’état de l’enum au lieu d’être l’une des valeurs de l’ensemble représenté par l’enum.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="7bb4d-127">✔️ fournissez une valeur égale à zéro sur les énumérations simples.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="7bb4d-128">Envisagez d’appeler la valeur comme « None ».</span><span class="sxs-lookup"><span data-stu-id="7bb4d-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="7bb4d-129">Si une telle valeur n’est pas appropriée pour cette énumération particulière, la valeur par défaut la plus courante pour l’énumération doit être assignée à la valeur sous-jacente de zéro.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="7bb4d-130">✔️ envisagez <xref:System.Int32> d’utiliser (valeur par défaut dans la plupart des langages de programmation) comme type sous-jacent d’une énumération, sauf si l’une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="7bb4d-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="7bb4d-131">L’énumération est une énumération d’indicateurs et vous avez plus de 32 indicateurs, ou vous prévoyez d’en avoir plus à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="7bb4d-132">Le type sous-jacent doit être différent <xref:System.Int32> de pour faciliter l’interopérabilité avec du code non managé qui attend des énumérations de taille différente.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="7bb4d-133">Un type sous-jacent plus petit entraînerait des économies substantielles dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="7bb4d-134">Si vous vous attendez à ce que l’énumération soit principalement utilisée comme argument pour le workflow de contrôle, la taille n’a pas de différence.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="7bb4d-135">Les économies de taille peuvent être significatives dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="7bb4d-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="7bb4d-136">Vous vous attendez à ce que l’énumération soit utilisée en tant que champ dans une classe ou une structure très fréquemment instanciée.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="7bb4d-137">Vous vous attendez à ce que les utilisateurs créent des tableaux ou des collections volumineux des instances d’énumération.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="7bb4d-138">Vous vous attendez à ce qu’un grand nombre d’instances de l’énumération soient sérialisées.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="7bb4d-139">Pour l’utilisation en mémoire, sachez que les objets managés sont toujours `DWORD` alignés. par conséquent, vous avez besoin de plusieurs enums ou d’autres petites structures dans une instance pour empaqueter une énumération plus petite avec afin de faire la différence, car la taille totale de l’instance est toujours arrondie à un `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="7bb4d-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="7bb4d-140">✔️ Nommez les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et des énumérations simples avec des noms au singulier ou des expressions nominales.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="7bb4d-141">❌ N’étendez pas <xref:System.Enum?displayProperty=nameWithType> directement.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="7bb4d-142"><xref:System.Enum?displayProperty=nameWithType> est un type spécial utilisé par le CLR pour créer des énumérations définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="7bb4d-143">La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="7bb4d-144">Par exemple, en C#, le `enum` mot clé est utilisé pour définir une énumération.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="7bb4d-145">Conception d’énumérations d’indicateur</span><span class="sxs-lookup"><span data-stu-id="7bb4d-145">Designing Flag Enums</span></span>

<span data-ttu-id="7bb4d-146">✔️ Appliquez <xref:System.FlagsAttribute?displayProperty=nameWithType> pour marquer les enums.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="7bb4d-147">N’appliquez pas cet attribut à des énumérations simples.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="7bb4d-148">✔️ Utilisez les puissances de deux pour les valeurs d’énumération d’indicateur afin qu’elles puissent être combinées librement à l’aide de l’opération or au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="7bb4d-149">✔️ envisagez de fournir des valeurs d’énumération spéciales pour les combinaisons d’indicateurs couramment utilisées.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="7bb4d-150">Les opérations au niveau du bit sont un concept avancé qui ne doit pas être nécessaire pour les tâches simples.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="7bb4d-151"><xref:System.IO.FileAccess.ReadWrite> est un exemple de cette valeur spéciale.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="7bb4d-152">❌ Évitez de créer des énumérations d’indicateur lorsque certaines combinaisons de valeurs ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="7bb4d-153">❌ Évitez d’utiliser des valeurs d’énumération d’indicateur de zéro, sauf si la valeur représente « tous les indicateurs sont désactivés » et s’il est nommé de manière appropriée, comme indiqué par l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="7bb4d-154">✔️ Nommez la valeur zéro des énumérations d’indicateur `None` .</span><span class="sxs-lookup"><span data-stu-id="7bb4d-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="7bb4d-155">Pour une énumération d’indicateur, la valeur doit toujours signifier que « tous les indicateurs sont effacés ».</span><span class="sxs-lookup"><span data-stu-id="7bb4d-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="7bb4d-156">Ajouter de la valeur aux enums</span><span class="sxs-lookup"><span data-stu-id="7bb4d-156">Adding Value to Enums</span></span>

<span data-ttu-id="7bb4d-157">Il est très courant de découvrir que vous devez ajouter des valeurs à une énumération une fois que vous l’avez déjà livrée.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="7bb4d-158">Il y a un problème potentiel de compatibilité des applications lorsque la valeur récemment ajoutée est retournée à partir d’une API existante, car les applications mal écrites peuvent ne pas gérer correctement la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="7bb4d-159">✔️ envisagez d’ajouter des valeurs aux enums, en dépit d’un faible risque de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="7bb4d-160">Si vous avez des données réelles sur les incompatibilités d’application provoquées par des ajouts à une énumération, envisagez d’ajouter une nouvelle API qui retourne les valeurs nouvelles et anciennes, et de déprécier l’ancienne API, qui doit continuer à retourner uniquement les anciennes valeurs.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="7bb4d-161">Cela permet de s’assurer que vos applications existantes restent compatibles.</span><span class="sxs-lookup"><span data-stu-id="7bb4d-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="7bb4d-162">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="7bb4d-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="7bb4d-163">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7bb4d-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7bb4d-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bb4d-164">See also</span></span>

- [<span data-ttu-id="7bb4d-165">Règles de conception de type</span><span class="sxs-lookup"><span data-stu-id="7bb4d-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="7bb4d-166">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="7bb4d-166">Framework Design Guidelines</span></span>](index.md)
