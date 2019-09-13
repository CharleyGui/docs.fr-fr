---
title: Gestion de version C# - Guide C#
description: Comprendre le fonctionnement de la gestion de version C# et .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926583"
---
# <a name="versioning-in-c"></a><span data-ttu-id="a162b-103">Gestion de versions en C\#</span><span class="sxs-lookup"><span data-stu-id="a162b-103">Versioning in C\#</span></span>

<span data-ttu-id="a162b-104">Dans ce didacticiel, vous allez apprendre la signification de la gestion de version .NET.</span><span class="sxs-lookup"><span data-stu-id="a162b-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="a162b-105">Vous découvrirez également les facteurs à prendre en compte dans le cadre du contrôle de version de votre bibliothèque et de sa mise à niveau vers une nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="a162b-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="a162b-106">Création de bibliothèques</span><span class="sxs-lookup"><span data-stu-id="a162b-106">Authoring Libraries</span></span>

<span data-ttu-id="a162b-107">En tant que développeur ayant créé des bibliothèques .NET pour une utilisation publique, vous avez probablement été confronté à des situations où vous deviez déployer de nouvelles mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a162b-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="a162b-108">Votre manière de procéder est très importante, car vous devez assurer une transition fluide du code existant vers la nouvelle version de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a162b-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="a162b-109">Voici quelques points à prendre en compte lors de la création d’une version :</span><span class="sxs-lookup"><span data-stu-id="a162b-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="a162b-110">Gestion sémantique de version</span><span class="sxs-lookup"><span data-stu-id="a162b-110">Semantic Versioning</span></span>

<span data-ttu-id="a162b-111">La [gestion sémantique de version](https://semver.org/) (SemVer en abrégé) est une convention d’affectation de noms appliquée à des versions de votre bibliothèque pour indiquer des événements jalons spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a162b-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="a162b-112">Dans l’idéal, les informations de version ajoutées à votre bibliothèque doivent aider les développeurs à déterminer la compatibilité avec les projets qui utilisent des versions antérieures de cette même bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a162b-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="a162b-113">L’approche la plus simple de SemVer est le format à 3 composants `MAJOR.MINOR.PATCH`, où :</span><span class="sxs-lookup"><span data-stu-id="a162b-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="a162b-114">`MAJOR` est incrémenté quand vous apportez des changements d’API incompatibles</span><span class="sxs-lookup"><span data-stu-id="a162b-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="a162b-115">`MINOR` est incrémenté quand vous ajoutez des fonctionnalités à compatibilité descendante</span><span class="sxs-lookup"><span data-stu-id="a162b-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="a162b-116">`PATCH` est incrémenté quand vous apportez des correctifs de bogues à compatibilité descendante</span><span class="sxs-lookup"><span data-stu-id="a162b-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="a162b-117">Il existe également des moyens de spécifier d’autres scénarios, tels que des préversions, lors de l’application des informations de version à votre bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="a162b-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="a162b-118">Compatibilité descendante</span><span class="sxs-lookup"><span data-stu-id="a162b-118">Backwards Compatibility</span></span>

<span data-ttu-id="a162b-119">Quand vous publiez de nouvelles versions de votre bibliothèque, l’une de vos principales préoccupations concerne la compatibilité descendante avec les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="a162b-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="a162b-120">Une nouvelle version de la bibliothèque est compatible au format source avec une version précédente si le code qui dépend de la version précédente est utilisable avec la nouvelle version une fois qu’il est recompilé.</span><span class="sxs-lookup"><span data-stu-id="a162b-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="a162b-121">Une nouvelle version de la bibliothèque est compatible au format binaire si une application qui dépendait de l’ancienne version est utilisable avec la nouvelle version sans recompilation.</span><span class="sxs-lookup"><span data-stu-id="a162b-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="a162b-122">Voici quelques éléments à prendre en compte quand vous tentez de maintenir la compatibilité descendante avec d’anciennes versions de votre bibliothèque  :</span><span class="sxs-lookup"><span data-stu-id="a162b-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="a162b-123">Méthodes virtuelles : quand vous rendez une méthode virtuelle non virtuelle dans la nouvelle version, cela signifie que les projets qui substituent cette méthode doivent être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a162b-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="a162b-124">Il s’agit là d’une modification avec rupture importante qui est vivement déconseillée.</span><span class="sxs-lookup"><span data-stu-id="a162b-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="a162b-125">Signatures de méthode : quand la mise à jour d’un comportement de méthode vous oblige à modifier également sa signature, vous devez créer à la place une surcharge afin que le code appelant cette méthode fonctionne toujours.</span><span class="sxs-lookup"><span data-stu-id="a162b-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="a162b-126">Vous pouvez toujours manipuler l’ancienne signature de méthode pour appeler la nouvelle signature de méthode afin que l’implémentation reste cohérente.</span><span class="sxs-lookup"><span data-stu-id="a162b-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="a162b-127">[Attribut obsolète](programming-guide/concepts/attributes/common-attributes.md#Obsolete) : vous pouvez utiliser cet attribut dans votre code pour spécifier des classes ou membres de classe dépréciés et susceptibles d’être supprimés dans les prochaines versions.</span><span class="sxs-lookup"><span data-stu-id="a162b-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="a162b-128">Cela garantit que les développeurs utilisant votre bibliothèque sont mieux préparés pour les modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="a162b-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="a162b-129">Arguments de méthode facultatifs : quand vous rendez obligatoires des arguments de méthode auparavant facultatifs ou modifiez leur valeur par défaut, tout le code qui ne fournit pas ces arguments doit être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a162b-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="a162b-130">Le fait de rendre obligatoires des arguments facultatifs doit avoir très peu d’effet en particulier si le comportement de la méthode ne change pas.</span><span class="sxs-lookup"><span data-stu-id="a162b-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="a162b-131">Plus il est facile pour vos utilisateurs d’effectuer la mise à niveau vers la nouvelle version de votre bibliothèque, plus il est probable qu’ils le feront rapidement.</span><span class="sxs-lookup"><span data-stu-id="a162b-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="a162b-132">Fichier de configuration de l'application</span><span class="sxs-lookup"><span data-stu-id="a162b-132">Application Configuration File</span></span>

<span data-ttu-id="a162b-133">En tant que développeur .NET, il est très probable que vous ayez rencontré [le fichier `app.config`](../framework/configure-apps/file-schema/index.md), présent dans la plupart des types de projets.</span><span class="sxs-lookup"><span data-stu-id="a162b-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="a162b-134">Ce simple fichier de configuration peut s’avérer très utile pour améliorer le déploiement de nouvelles mises à jour.</span><span class="sxs-lookup"><span data-stu-id="a162b-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="a162b-135">Vous devez généralement concevoir vos bibliothèques de sorte que les informations qui sont susceptibles de changer régulièrement soient stockées dans le fichier `app.config` ; ainsi, quand ces informations sont mises à jour, le fichier de configuration des anciennes versions doit uniquement être remplacé par le nouveau sans que la recompilation de la bibliothèque ne soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a162b-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="a162b-136">Utilisation des bibliothèques</span><span class="sxs-lookup"><span data-stu-id="a162b-136">Consuming Libraries</span></span>

<span data-ttu-id="a162b-137">En tant que développeur qui utilise les bibliothèques .NET générées par d’autres développeurs, vous savez probablement qu’une nouvelle version d’une bibliothèque peut ne pas être totalement compatible avec votre projet et vous pouvez souvent être obligé de mettre à jour votre code pour vous adapter à ces modifications.</span><span class="sxs-lookup"><span data-stu-id="a162b-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="a162b-138">Heureusement pour vous, C# et l’écosystème .NET sont fournis avec des fonctionnalités et techniques qui nous permettent de mettre facilement à jour notre application pour utiliser les nouvelles versions de bibliothèques qui peuvent présenter des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="a162b-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="a162b-139">Redirection des liaisons d'assembly</span><span class="sxs-lookup"><span data-stu-id="a162b-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="a162b-140">Vous pouvez utiliser le fichier `app.config` pour mettre à jour la version d’une bibliothèque que votre application emploie.</span><span class="sxs-lookup"><span data-stu-id="a162b-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="a162b-141">En ajoutant un élément nommé [*redirection de liaison*](../framework/configure-apps/redirect-assembly-versions.md), vous pouvez utiliser la nouvelle version de bibliothèque sans avoir à recompiler votre application.</span><span class="sxs-lookup"><span data-stu-id="a162b-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="a162b-142">L’exemple suivant montre comment vous devez mettre à jour le fichier `app.config` de votre application pour utiliser la version corrective `1.0.1` de `ReferencedLibrary` au lieu de la version `1.0.0` avec laquelle il a été compilé à l’origine.</span><span class="sxs-lookup"><span data-stu-id="a162b-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="a162b-143">Cette approche fonctionne uniquement si la nouvelle version de `ReferencedLibrary` est compatible au format binaire avec votre application.</span><span class="sxs-lookup"><span data-stu-id="a162b-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="a162b-144">Consultez la section [Compatibilité descendante](#backwards-compatibility) ci-dessus pour connaître les changements à rechercher lors de la détermination de la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="a162b-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="a162b-145">new</span><span class="sxs-lookup"><span data-stu-id="a162b-145">new</span></span>

<span data-ttu-id="a162b-146">Vous utilisez le modificateur `new` pour masquer les membres hérités d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="a162b-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="a162b-147">Il s’agit d’une façon pour les classes dérivées de pouvoir répondre aux mises à jour dans les classes de base.</span><span class="sxs-lookup"><span data-stu-id="a162b-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="a162b-148">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a162b-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="a162b-149">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="a162b-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="a162b-150">Dans l’exemple ci-dessus, vous pouvez voir comment `DerivedClass` masque la méthode `MyMethod` présente dans `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a162b-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="a162b-151">Cela signifie que, quand une classe de base dans la nouvelle version d’une bibliothèque ajoute un membre qui existe déjà dans votre classe dérivée, vous pouvez simplement utiliser le modificateur `new` sur le membre de la classe dérivée pour masquer le membre de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a162b-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="a162b-152">Quand aucun modificateur `new` n’est spécifié, une classe dérivée masque par défaut des membres en conflit dans une classe de base ; même si un avertissement du compilateur est généré, le code est toujours compilé.</span><span class="sxs-lookup"><span data-stu-id="a162b-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="a162b-153">Cela signifie que le fait d’ajouter simplement de nouveaux membres à une classe existante rend cette nouvelle version de votre bibliothèque compatible au format source et binaire avec le code qui en dépend.</span><span class="sxs-lookup"><span data-stu-id="a162b-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="a162b-154">override</span><span class="sxs-lookup"><span data-stu-id="a162b-154">override</span></span>

<span data-ttu-id="a162b-155">Le modificateur `override` indique qu’une implémentation dérivée étend l’implémentation d’un membre de classe de base au lieu de la masquer.</span><span class="sxs-lookup"><span data-stu-id="a162b-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="a162b-156">Le modificateur `virtual` doit être appliqué au membre de classe de base.</span><span class="sxs-lookup"><span data-stu-id="a162b-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="a162b-157">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="a162b-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="a162b-158">Le modificateur `override` est évalué au moment de la compilation et génère une erreur s’il ne trouve pas un membre virtuel à substituer.</span><span class="sxs-lookup"><span data-stu-id="a162b-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="a162b-159">Votre connaissance des techniques présentées et des situations dans lesquelles les utiliser sera très utile pour passer en douceur d’une version de bibliothèque à une autre.</span><span class="sxs-lookup"><span data-stu-id="a162b-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
 