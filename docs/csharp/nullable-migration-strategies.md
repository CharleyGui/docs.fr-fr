---
title: Mettez à jour votre base de code pour utiliser des types de référence nuls
description: Choisissez la meilleure stratégie pour mettre à niveau votre base de code pour utiliser des types de référence nuls.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: b4a10863aea5c47b47c2a017afb20786b1e67528
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103526"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="c559f-103">Mettre à jour les bibliothèques pour qu’elles utilisent des types de référence nuls et communiquent des règles in annulables aux appelants</span><span class="sxs-lookup"><span data-stu-id="c559f-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="c559f-104">L’ajout de types de [référence in annulables](nullable-references.md) signifie que vous pouvez déclarer si une `null` valeur est autorisée ou attendue pour chaque variable.</span><span class="sxs-lookup"><span data-stu-id="c559f-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="c559f-105">En outre, vous pouvez appliquer un `AllowNull` `DisallowNull`certain `MaybeNull` `NotNull`nombre `NotNullWhen` `MaybeNullWhen`d’attributs: , , , , , et `NotNullIfNotNull` de décrire complètement les états nuls de l’argumentation et les valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="c559f-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="c559f-106">Cela offre une grande expérience que vous écrivez du code.</span><span class="sxs-lookup"><span data-stu-id="c559f-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="c559f-107">Vous obtenez des avertissements si une variable `null`non-nullable pourrait être définie à .</span><span class="sxs-lookup"><span data-stu-id="c559f-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="c559f-108">Vous obtenez des avertissements si une variable nulle n’est pas vérifiée non vérifiée avant de la déreférencer.</span><span class="sxs-lookup"><span data-stu-id="c559f-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="c559f-109">La mise à jour de vos bibliothèques peut prendre du temps, mais les retombées en valent la peine.</span><span class="sxs-lookup"><span data-stu-id="c559f-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="c559f-110">Plus vous fournissez d’informations au `null` compilateur sur le *moment où* une valeur est autorisée ou interdite, les meilleurs avertissements que les utilisateurs de votre API obtiendront.</span><span class="sxs-lookup"><span data-stu-id="c559f-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="c559f-111">Commençons par un exemple familier.</span><span class="sxs-lookup"><span data-stu-id="c559f-111">Let's start with a familiar example.</span></span> <span data-ttu-id="c559f-112">Imaginez que votre bibliothèque dispose de l’API suivante pour récupérer une chaîne de ressources :</span><span class="sxs-lookup"><span data-stu-id="c559f-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="c559f-113">L’exemple précédent `Try*` suit le modèle familier en .NET.</span><span class="sxs-lookup"><span data-stu-id="c559f-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="c559f-114">Il existe deux arguments de référence `key` pour `message` cette API : le et le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c559f-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="c559f-115">Cette API a les règles suivantes relatives à l’annulation de ces arguments :</span><span class="sxs-lookup"><span data-stu-id="c559f-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="c559f-116">Les appelants `null` ne devraient pas `key`passer comme l’argument pour .</span><span class="sxs-lookup"><span data-stu-id="c559f-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="c559f-117">Les appelants peuvent passer une `null` variable dont `message`la valeur est comme l’argument pour .</span><span class="sxs-lookup"><span data-stu-id="c559f-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="c559f-118">Si `TryGetMessage` la `true`méthode revient, la valeur de `message` n’est pas nulle.</span><span class="sxs-lookup"><span data-stu-id="c559f-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="c559f-119">Si la valeur `false,` de `message` rendement est la valeur de (et son état nul) est nulle.</span><span class="sxs-lookup"><span data-stu-id="c559f-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="c559f-120">La règle `key` pour peut être entièrement `key` exprimée par le type variable: devrait être un type de référence non-nullable.</span><span class="sxs-lookup"><span data-stu-id="c559f-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="c559f-121">Le `message` paramètre est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="c559f-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="c559f-122">Il `null` permet comme argument, mais garantit que, sur le succès, cet `out` argument n’est pas nul.</span><span class="sxs-lookup"><span data-stu-id="c559f-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="c559f-123">Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.</span><span class="sxs-lookup"><span data-stu-id="c559f-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="c559f-124">La mise à jour de votre bibliothèque `?` pour les références annulées nécessite plus que saupoudrer sur certaines des variables et des noms de type.</span><span class="sxs-lookup"><span data-stu-id="c559f-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="c559f-125">L’exemple précédent montre que vous devez examiner vos API et tenir compte de vos attentes pour chaque argument d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c559f-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="c559f-126">Tenez compte des garanties pour `out` la `ref` valeur de retour, et tout ou argumentation lors du retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c559f-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="c559f-127">Communiquez ensuite ces règles au compilateur, et le compilateur fournira des avertissements lorsque les appelants ne respectent pas ces règles.</span><span class="sxs-lookup"><span data-stu-id="c559f-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="c559f-128">Ce travail prend du temps.</span><span class="sxs-lookup"><span data-stu-id="c559f-128">This work takes time.</span></span> <span data-ttu-id="c559f-129">Commençons par des stratégies pour rendre votre bibliothèque ou votre application in annulable, tout en équilibrant d’autres exigences et livrables.</span><span class="sxs-lookup"><span data-stu-id="c559f-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="c559f-130">Vous verrez comment équilibrer le développement en cours permettant des types de référence nuls.</span><span class="sxs-lookup"><span data-stu-id="c559f-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="c559f-131">Vous apprendrez des défis pour les définitions de type générique.</span><span class="sxs-lookup"><span data-stu-id="c559f-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="c559f-132">Vous apprendrez à appliquer des attributs pour décrire les conditions préalables et post-conditions sur les API individuelles.</span><span class="sxs-lookup"><span data-stu-id="c559f-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="c559f-133">Choisissez une stratégie pour les types de référence nuls</span><span class="sxs-lookup"><span data-stu-id="c559f-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="c559f-134">Le premier choix est de savoir si les types de référence nuls doivent être allumés ou annulés par défaut.</span><span class="sxs-lookup"><span data-stu-id="c559f-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="c559f-135">Vous avez deux stratégies :</span><span class="sxs-lookup"><span data-stu-id="c559f-135">You have two strategies:</span></span>

- <span data-ttu-id="c559f-136">Activez les types de référence nuls pour l’ensemble du projet et désactivez-le dans un code qui n’est pas prêt.</span><span class="sxs-lookup"><span data-stu-id="c559f-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="c559f-137">N’activez que les types de référence inquérables pour le code qui a été annoté pour les types de référence annulés.</span><span class="sxs-lookup"><span data-stu-id="c559f-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="c559f-138">La première stratégie fonctionne mieux lorsque vous ajoutez d’autres fonctionnalités à la bibliothèque lorsque vous la mettez à jour pour les types de référence nuls.</span><span class="sxs-lookup"><span data-stu-id="c559f-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="c559f-139">Tout nouveau développement est invenu conscient.</span><span class="sxs-lookup"><span data-stu-id="c559f-139">All new development is nullable aware.</span></span> <span data-ttu-id="c559f-140">Lorsque vous mettez à jour le code existant, vous activez des types de référence nuls dans ces classes.</span><span class="sxs-lookup"><span data-stu-id="c559f-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="c559f-141">Suite à cette première stratégie, vous faites ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c559f-141">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="c559f-142">Activez les types de référence nuls pour l’ensemble du projet en ajoutant l’élément `<Nullable>enable</Nullable>` à vos fichiers *csproj.*</span><span class="sxs-lookup"><span data-stu-id="c559f-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="c559f-143">Ajoutez `#nullable disable` le pragma à chaque fichier source de votre projet.</span><span class="sxs-lookup"><span data-stu-id="c559f-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="c559f-144">Lorsque vous travaillez sur chaque fichier, retirez le pragma et adressez les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c559f-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="c559f-145">Cette première stratégie a plus de travail à l’avance pour ajouter le pragma à chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="c559f-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="c559f-146">L’avantage est que chaque nouveau fichier de code ajouté au projet sera annulé activé.</span><span class="sxs-lookup"><span data-stu-id="c559f-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="c559f-147">Tout nouveau travail sera in nullable au courant; seul le code existant doit être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="c559f-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="c559f-148">La deuxième stratégie fonctionne mieux si la bibliothèque est généralement stable, et l’objectif principal de l’élaboration est d’adopter des types de référence nuls.</span><span class="sxs-lookup"><span data-stu-id="c559f-148">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="c559f-149">Vous activez les types de référence incontables au fur et à mesure que vous annotez les API.</span><span class="sxs-lookup"><span data-stu-id="c559f-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="c559f-150">Lorsque vous avez terminé, vous activez des types de référence nuls pour l’ensemble du projet.</span><span class="sxs-lookup"><span data-stu-id="c559f-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="c559f-151">Suite à cette deuxième stratégie, vous faites ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c559f-151">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="c559f-152">Ajoutez `#nullable enable` le pragma au fichier que vous souhaitez rendre nul possible.</span><span class="sxs-lookup"><span data-stu-id="c559f-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="c559f-153">Adressez tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c559f-153">Address any warnings.</span></span>
1. <span data-ttu-id="c559f-154">Poursuivez ces deux premières étapes jusqu’à ce que vous ayez rendu la bibliothèque nulle au courant.</span><span class="sxs-lookup"><span data-stu-id="c559f-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="c559f-155">Activez les types nuls pour `<Nullable>enable</Nullable>` l’ensemble du projet en ajoutant l’élément à vos fichiers *csproj.*</span><span class="sxs-lookup"><span data-stu-id="c559f-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="c559f-156">Retirez `#nullable enable` les pragmas, car ils ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c559f-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="c559f-157">Cette deuxième stratégie a moins de travail à l’avance.</span><span class="sxs-lookup"><span data-stu-id="c559f-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="c559f-158">Le compromis est que la première tâche lorsque vous créez un nouveau fichier est d’ajouter le pragma et le rendre invenu possible.</span><span class="sxs-lookup"><span data-stu-id="c559f-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="c559f-159">Si des développeurs de votre équipe oublient, ce nouveau code est maintenant dans l’arriéré de travail pour rendre tout le code infirament.</span><span class="sxs-lookup"><span data-stu-id="c559f-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="c559f-160">Les stratégies que vous choisissez dépendent de l’ampleur du développement actif de votre projet.</span><span class="sxs-lookup"><span data-stu-id="c559f-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="c559f-161">Plus votre projet est mature et stable, meilleure est la deuxième stratégie.</span><span class="sxs-lookup"><span data-stu-id="c559f-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="c559f-162">Plus il y a de fonctionnalités développées, meilleure est la première stratégie.</span><span class="sxs-lookup"><span data-stu-id="c559f-162">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="c559f-163">Les avertissements annulés devraient-ils introduire des changements de rupture?</span><span class="sxs-lookup"><span data-stu-id="c559f-163">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="c559f-164">Avant d’activer les types de référence annulables, les variables sont considérées comme *nulles inconscientes.*</span><span class="sxs-lookup"><span data-stu-id="c559f-164">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="c559f-165">Une fois que vous activez les types de référence annulés, toutes ces variables ne sont *pas annulables.*</span><span class="sxs-lookup"><span data-stu-id="c559f-165">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="c559f-166">Le compilateur émettra des avertissements si ces variables ne sont pas parasitées à des valeurs non nulles.</span><span class="sxs-lookup"><span data-stu-id="c559f-166">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="c559f-167">Une autre source probable d’avertissements est les valeurs de rendement lorsque la valeur n’a pas été parasécée.</span><span class="sxs-lookup"><span data-stu-id="c559f-167">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="c559f-168">La première étape pour traiter les avertissements `?` de compilateur est d’utiliser des annotations sur les types de paramètres et de retour pour indiquer quand les arguments ou les valeurs de retour peuvent être nuls.</span><span class="sxs-lookup"><span data-stu-id="c559f-168">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="c559f-169">Lorsque les variables de référence ne doivent pas être nulles, la déclaration initiale est correcte.</span><span class="sxs-lookup"><span data-stu-id="c559f-169">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="c559f-170">Comme vous le faites, votre objectif n’est pas seulement de fixer les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c559f-170">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="c559f-171">L’objectif le plus important est de faire comprendre au compilateur votre intention de valeurs nulles potentielles.</span><span class="sxs-lookup"><span data-stu-id="c559f-171">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="c559f-172">Lorsque vous examinez les avertissements, vous arrivez à votre prochaine décision majeure pour votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="c559f-172">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="c559f-173">Voulez-vous envisager de modifier les signatures API pour communiquer plus clairement votre intention de conception?</span><span class="sxs-lookup"><span data-stu-id="c559f-173">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="c559f-174">Une meilleure signature API pour la `TryGetMessage` méthode examinée plus tôt pourrait être :</span><span class="sxs-lookup"><span data-stu-id="c559f-174">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="c559f-175">La valeur de rendement indique le succès ou l’échec, et porte la valeur si la valeur a été trouvée.</span><span class="sxs-lookup"><span data-stu-id="c559f-175">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="c559f-176">Dans de nombreux cas, la modification des signatures API peut améliorer la façon dont elles communiquent des valeurs nulles.</span><span class="sxs-lookup"><span data-stu-id="c559f-176">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="c559f-177">Toutefois, pour les bibliothèques publiques ou les bibliothèques dotées de grandes bases d’utilisateurs, vous préférerez peut-être ne pas introduire de modifications de signatures de l’API.</span><span class="sxs-lookup"><span data-stu-id="c559f-177">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="c559f-178">Pour ces cas, et d’autres modèles communs, vous pouvez appliquer des `null`attributs pour définir plus clairement quand un argument ou une valeur de retour peut être .</span><span class="sxs-lookup"><span data-stu-id="c559f-178">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="c559f-179">Que vous envisagez ou non de changer la surface de votre API, vous constaterez `null` probablement que les annotations de type à elles seules ne sont pas suffisantes pour décrire les valeurs pour les arguments ou les valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="c559f-179">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="c559f-180">Dans ces cas, vous pouvez appliquer des attributs pour décrire plus clairement une API.</span><span class="sxs-lookup"><span data-stu-id="c559f-180">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="c559f-181">Les attributs prolongent les annotations de type</span><span class="sxs-lookup"><span data-stu-id="c559f-181">Attributes extend type annotations</span></span>

<span data-ttu-id="c559f-182">Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’état nul des variables.</span><span class="sxs-lookup"><span data-stu-id="c559f-182">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="c559f-183">Tout le code que vous avez écrit avant que le C 8 n’introduise des types de référence nuls *était nul inconscient.*</span><span class="sxs-lookup"><span data-stu-id="c559f-183">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="c559f-184">Cela signifie que toute variable de type de référence peut être nulle, mais les contrôles nuls ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c559f-184">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="c559f-185">Une fois que votre code est *infirampable au courant,* ces règles changent.</span><span class="sxs-lookup"><span data-stu-id="c559f-185">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="c559f-186">Les types de `null` référence ne doivent jamais être la `null` valeur, et les types de référence nuls doivent être vérifiés avant d’être déreférés.</span><span class="sxs-lookup"><span data-stu-id="c559f-186">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="c559f-187">Les règles de vos API sont probablement plus `TryGetValue` compliquées, comme vous l’avez vu avec le scénario API.</span><span class="sxs-lookup"><span data-stu-id="c559f-187">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="c559f-188">Beaucoup de vos API ont des règles plus complexes pour quand les variables peuvent ou ne peuvent pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="c559f-188">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="c559f-189">Dans ces cas, vous utiliserez des attributs pour exprimer ces règles.</span><span class="sxs-lookup"><span data-stu-id="c559f-189">In these cases, you'll use attributes to express those rules.</span></span> <span data-ttu-id="c559f-190">Les attributs qui décrivent la sémantique de votre API se trouvent dans l’article sur [les attributs qui ont un impact d’analyse nulle](./language-reference/attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="c559f-190">The attributes that describe the semantics of your API are found in the article on [Attributes that impact nullable analysis](./language-reference/attributes/nullable-analysis.md).</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="c559f-191">Définitions génériques et nullité</span><span class="sxs-lookup"><span data-stu-id="c559f-191">Generic definitions and nullability</span></span>

<span data-ttu-id="c559f-192">Communiquer correctement l’état nul des types génériques et des méthodes génériques nécessite un soin particulier.</span><span class="sxs-lookup"><span data-stu-id="c559f-192">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="c559f-193">Cela découle du fait qu’un type de valeur nul et un type de référence nul sont fondamentalement différents.</span><span class="sxs-lookup"><span data-stu-id="c559f-193">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="c559f-194">Un `int?` est synonyme `Nullable<int>`de `string?` , `string` alors qu’il est avec un attribut ajouté par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="c559f-194">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="c559f-195">Le résultat est que le compilateur ne `T?` peut `T` pas `class` générer `struct`un code correct pour sans savoir si est a ou a .</span><span class="sxs-lookup"><span data-stu-id="c559f-195">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="c559f-196">Cela ne signifie pas que vous ne pouvez pas utiliser un type nul (type de valeur ou de type de référence) comme argument de type pour un type générique fermé.</span><span class="sxs-lookup"><span data-stu-id="c559f-196">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="c559f-197">Les `List<string?>` `List<int?>` deux et sont des `List<T>`instantanés valides de .</span><span class="sxs-lookup"><span data-stu-id="c559f-197">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="c559f-198">Ce que cela signifie, c’est que vous ne pouvez pas utiliser `T?` dans une classe générique ou une déclaration de méthode sans contraintes.</span><span class="sxs-lookup"><span data-stu-id="c559f-198">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="c559f-199">Par exemple, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> ne sera pas `T?`changé pour revenir .</span><span class="sxs-lookup"><span data-stu-id="c559f-199">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="c559f-200">Vous pouvez surmonter cette limitation `struct` `class` en ajoutant soit la contrainte.</span><span class="sxs-lookup"><span data-stu-id="c559f-200">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="c559f-201">Avec l’une ou l’autre de ces contraintes, le compilateur sait comment générer du code pour les deux `T` et `T?`.</span><span class="sxs-lookup"><span data-stu-id="c559f-201">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="c559f-202">Vous pouvez restreindre les types utilisés pour un argument de type générique pour être des types non-nullables.</span><span class="sxs-lookup"><span data-stu-id="c559f-202">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="c559f-203">Vous pouvez le faire `notnull` en ajoutant la contrainte sur cet argument de type.</span><span class="sxs-lookup"><span data-stu-id="c559f-203">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="c559f-204">Lorsque cette contrainte est appliquée, l’argument type ne doit pas être un type nul.</span><span class="sxs-lookup"><span data-stu-id="c559f-204">When that constraint is applied, the type argument must not be a nullable type.</span></span>