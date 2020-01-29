---
title: Changements cassants et bibliothèques .NET
description: Recommandations relatives aux bonnes pratiques pour parcourir les changements cassants lors de la création de bibliothèques .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731468"
---
# <a name="breaking-changes"></a><span data-ttu-id="25492-103">Modifications avec rupture</span><span class="sxs-lookup"><span data-stu-id="25492-103">Breaking changes</span></span>

<span data-ttu-id="25492-104">Il est important pour une bibliothèque .NET de trouver un équilibre entre la stabilité pour les utilisateurs existants et l’innovation pour l’avenir.</span><span class="sxs-lookup"><span data-stu-id="25492-104">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="25492-105">Les auteurs de bibliothèques tendent à refactoriser et repenser le code jusqu’à ce qu’il soit parfait, mais les changements cassants peuvent avoir un impact négatif sur vos utilisateurs existants, surtout pour les bibliothèques de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="25492-105">Library authors lean towards refactoring and rethinking code until it's perfect, but breaking your existing users has a negative impact, especially for low-level libraries.</span></span>

## <a name="project-types-and-breaking-changes"></a><span data-ttu-id="25492-106">Types de projets et changements cassants</span><span class="sxs-lookup"><span data-stu-id="25492-106">Project types and breaking changes</span></span>

<span data-ttu-id="25492-107">La façon dont une bibliothèque est utilisée par la communauté .NET modifie l’effet des changements cassants sur les développeurs utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="25492-107">How a library is used by the .NET community changes the effect of breaking changes on end-user developers.</span></span>

- <span data-ttu-id="25492-108">Les **bibliothèques de bas niveau et de niveau intermédiaire** comme les sérialiseurs, les analyseurs HTML, les outils de mappage objet-relationnel de base de données ou les frameworks web, sont les plus affectées par les changements cassants.</span><span class="sxs-lookup"><span data-stu-id="25492-108">**Low and middle-level libraries** like a serializer, HTML parser, database object-relational mapper, or web framework are the most affected by breaking changes.</span></span>

  <span data-ttu-id="25492-109">Les packages de modules sont utilisés par les développeurs utilisateurs finaux pour générer des applications et par d’autres bibliothèques comme dépendances NuGet.</span><span class="sxs-lookup"><span data-stu-id="25492-109">Building block packages are used by end-user developers to build applications, and by other libraries as NuGet dependencies.</span></span> <span data-ttu-id="25492-110">Par exemple, vous créez une application et utilisez un client open source pour appeler un service web.</span><span class="sxs-lookup"><span data-stu-id="25492-110">For example, you're building an application and are using an open-source client to call a web service.</span></span> <span data-ttu-id="25492-111">Une mise à jour cassante apportée à une dépendance qu’utilise le client n’est pas quelque chose que vous pouvez résoudre.</span><span class="sxs-lookup"><span data-stu-id="25492-111">A breaking update to a dependency the client uses isn't something you can fix.</span></span> <span data-ttu-id="25492-112">C’est le client open source qui doit être changé, mais vous n’avez aucun contrôle là-dessus.</span><span class="sxs-lookup"><span data-stu-id="25492-112">It's the open-source client that needs to be changed and you have no control over it.</span></span> <span data-ttu-id="25492-113">Vous devez rechercher des versions compatibles des bibliothèques ou envoyer un correctif à la bibliothèque cliente et attendre une nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="25492-113">You have to find compatible versions of the libraries or submit a fix to the client library and wait for a new version.</span></span> <span data-ttu-id="25492-114">Le pire des cas se présente si vous voulez utiliser deux bibliothèques qui dépendent de versions mutuellement incompatibles d’une troisième bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="25492-114">The worst-case situation is if you want to use two libraries that depend on mutually incompatible versions of a third library.</span></span>

- <span data-ttu-id="25492-115">Les **bibliothèques de haut niveau** comme les suites de contrôles d’interface utilisateur sont moins sensibles aux changements cassants.</span><span class="sxs-lookup"><span data-stu-id="25492-115">**High-level libraries** like a suite of UI controls are less sensitive to breaking changes.</span></span>

  <span data-ttu-id="25492-116">Les bibliothèques de haut niveau sont directement référencées dans une application pour l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="25492-116">High-level libraries are directly referenced in an end-user application.</span></span> <span data-ttu-id="25492-117">En cas de changements cassants, le développeur peut choisir de procéder à la mise à jour vers la dernière version ou modifier son application pour les utiliser.</span><span class="sxs-lookup"><span data-stu-id="25492-117">If breaking changes occur, the developer can choose to update to the latest version, or can modify their application to work with the breaking change.</span></span>

<span data-ttu-id="25492-118">✔️ Pensez à la façon dont votre bibliothèque sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="25492-118">✔️ DO think about how your library will be used.</span></span> <span data-ttu-id="25492-119">Quel sera l’effet des changements cassants sur les applications et les bibliothèques qui l’utilisent ?</span><span class="sxs-lookup"><span data-stu-id="25492-119">What effect will breaking changes have on applications and libraries that use it?</span></span>

<span data-ttu-id="25492-120">✔️ réduire les modifications avec rupture lors du développement d’une bibliothèque .NET de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="25492-120">✔️ DO minimize breaking changes when developing a low-level .NET library.</span></span>

<span data-ttu-id="25492-121">✔️ envisagez de publier une réécriture majeure d’une bibliothèque en tant que nouveau package NuGet.</span><span class="sxs-lookup"><span data-stu-id="25492-121">✔️ CONSIDER publishing a major rewrite of a library as a new NuGet package.</span></span>

## <a name="types-of-breaking-changes"></a><span data-ttu-id="25492-122">Types de changements cassants</span><span class="sxs-lookup"><span data-stu-id="25492-122">Types of breaking changes</span></span>

<span data-ttu-id="25492-123">Les changements cassants sont répartis en différentes catégories et n’ont pas tous le même impact.</span><span class="sxs-lookup"><span data-stu-id="25492-123">Breaking changes fall into different categories and aren't equally impactful.</span></span>

### <a name="source-breaking-change"></a><span data-ttu-id="25492-124">Changement cassant source</span><span class="sxs-lookup"><span data-stu-id="25492-124">Source breaking change</span></span>

<span data-ttu-id="25492-125">Un changement cassant source n’affecte pas l’exécution du programme, mais provoque des erreurs de compilation la prochaine fois que l’application est recompilée.</span><span class="sxs-lookup"><span data-stu-id="25492-125">A source breaking change doesn't affect program execution but will cause compilation errors the next time the application is recompiled.</span></span> <span data-ttu-id="25492-126">Par exemple, une nouvelle surcharge peut créer une ambiguïté dans les appels de méthode qui étaient précédemment non équivoques, ou un paramètre renommé peut casser des appelants qui utilisent des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="25492-126">For example, a new overload can create an ambiguity in method calls that were unambiguous previously, or a renamed parameter will break callers that use named parameters.</span></span>

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

<span data-ttu-id="25492-127">Comme un changement cassant source est uniquement nuisible quand les développeurs recompilent leurs applications, il s’agit de celui qui entraîne le moins de perturbations.</span><span class="sxs-lookup"><span data-stu-id="25492-127">Because a source breaking change is only harmful when developers recompile their applications, it's the least disruptive breaking change.</span></span> <span data-ttu-id="25492-128">Les développeurs peuvent facilement résoudre leur propre code source rompu.</span><span class="sxs-lookup"><span data-stu-id="25492-128">Developers can fix their own broken source code easily.</span></span>

### <a name="behavior-breaking-change"></a><span data-ttu-id="25492-129">Changement cassant de comportement</span><span class="sxs-lookup"><span data-stu-id="25492-129">Behavior breaking change</span></span>

<span data-ttu-id="25492-130">Les changements de comportement sont le type le plus courant de changement cassant : presque n’importe quel changement de comportement peut impacter une personne.</span><span class="sxs-lookup"><span data-stu-id="25492-130">Behavior changes are the most common type of breaking change: almost any change in behavior could break someone.</span></span> <span data-ttu-id="25492-131">Les changements apportés à votre bibliothèque, comme les signatures de méthode, les exceptions levées ou les formats de données d’entrée ou de sortie, peuvent tous avoir un impact négatif sur les consommateurs de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="25492-131">Changes to your library, such as method signatures, exceptions thrown or input or output data formats, could all negatively impact your library consumers.</span></span> <span data-ttu-id="25492-132">Même un correctif de bogue peut être considéré comme un changement cassant si les utilisateurs s’appuyaient sur le comportement précédemment rompu.</span><span class="sxs-lookup"><span data-stu-id="25492-132">Even a bug fix can qualify as a breaking change if users relied on the previously broken behavior.</span></span>

<span data-ttu-id="25492-133">L’ajout de fonctionnalités et l’amélioration des comportements médiocres sont une bonne chose, mais la mise à niveau peut s’avérer très difficile pour les utilisateurs existants sans les précautions nécessaires.</span><span class="sxs-lookup"><span data-stu-id="25492-133">Adding features and improving bad behaviors is a good thing, but without care it can make it very hard for existing users to upgrade.</span></span> <span data-ttu-id="25492-134">Une approche pour aider les développeurs à gérer les changements cassants de comportement consiste à les masquer derrière des paramètres.</span><span class="sxs-lookup"><span data-stu-id="25492-134">One approach to helping developers deal with behavior breaking changes is to hide them behind settings.</span></span> <span data-ttu-id="25492-135">Les paramètres permettent aux développeurs d’effectuer la mise à jour vers la dernière version de votre bibliothèque tout en choisissant d’adhérer ou non aux changements cassants.</span><span class="sxs-lookup"><span data-stu-id="25492-135">Settings let developers update to the latest version of your library while at the same time choosing to opt in or opt out of breaking changes.</span></span> <span data-ttu-id="25492-136">Cette stratégie permet aux développeurs de rester à jour tout en permettant à leur code de consommation de s’adapter au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="25492-136">This strategy lets developers stay up to date while letting their consuming code adapt over time.</span></span>

<span data-ttu-id="25492-137">Par exemple, ASP.NET Core MVC présente le concept d’une [version de compatibilité](/aspnet/core/mvc/compatibility-version) qui modifie les fonctionnalités activées et désactivées sur `MvcOptions`.</span><span class="sxs-lookup"><span data-stu-id="25492-137">For example, ASP.NET Core MVC has the concept of a [compatibility version](/aspnet/core/mvc/compatibility-version) that modifies the features enabled and disabled on `MvcOptions`.</span></span>

<span data-ttu-id="25492-138">✔️ envisagez de laisser les nouvelles fonctionnalités désactivées par défaut, si elles affectent les utilisateurs existants, et laissez les développeurs s’abonner à la fonctionnalité avec un paramètre.</span><span class="sxs-lookup"><span data-stu-id="25492-138">✔️ CONSIDER leaving new features off by default, if they affect existing users, and let developers opt in to the feature with a setting.</span></span>

### <a name="binary-breaking-change"></a><span data-ttu-id="25492-139">Changement cassant binaire</span><span class="sxs-lookup"><span data-stu-id="25492-139">Binary breaking change</span></span>

<span data-ttu-id="25492-140">Un changement cassant binaire se produit quand vous modifiez l’API publique de votre bibliothèque ; les assemblys compilés avec des versions antérieures de votre bibliothèque ne sont plus en mesure d’appeler l’API.</span><span class="sxs-lookup"><span data-stu-id="25492-140">A binary breaking change happens when you change the public API of your library, so assemblies compiled against older versions of your library are no longer able to call the API.</span></span> <span data-ttu-id="25492-141">Par exemple, la modification de la signature d’une méthode en ajoutant un nouveau paramètre amène les assemblys compilés avec la version antérieure de la bibliothèque à lever une <xref:System.MissingMethodException>.</span><span class="sxs-lookup"><span data-stu-id="25492-141">For example, changing a method's signature by adding a new parameter will cause assemblies compiled against the older version of the library to throw a <xref:System.MissingMethodException>.</span></span>

<span data-ttu-id="25492-142">Un changement cassant binaire peut également casser un **assembly entier**.</span><span class="sxs-lookup"><span data-stu-id="25492-142">A binary breaking change can also break an **entire assembly**.</span></span> <span data-ttu-id="25492-143">Le renommage d’un assembly avec `AssemblyName` change l’identité de l’assembly, de même que l’ajout, la suppression ou le changement de la clé d’affectation de noms forts de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="25492-143">Renaming an assembly with `AssemblyName` will change the assembly's identity, as will adding, removing, or changing the assembly's strong naming key.</span></span> <span data-ttu-id="25492-144">Un changement de l’identité d’un assembly va casser tout le code compilé qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="25492-144">A change of an assembly's identity will break all compiled code that uses it.</span></span>

<span data-ttu-id="25492-145">❌ ne modifiez pas un nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="25492-145">❌ DO NOT change an assembly name.</span></span>

<span data-ttu-id="25492-146">❌ n’ajoutez pas, ne supprimez pas ou ne modifiez pas la clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="25492-146">❌ DO NOT add, remove, or change the strong naming key.</span></span>

<span data-ttu-id="25492-147">✔️ envisagez d’utiliser des classes de base abstraites au lieu d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="25492-147">✔️ CONSIDER using abstract base classes instead of interfaces.</span></span>

> <span data-ttu-id="25492-148">L’ajout de n’importe quel élément à une interface entraîne l’échec des types existants qui l’implémentent.</span><span class="sxs-lookup"><span data-stu-id="25492-148">Adding anything to an interface will cause existing types that implement it to fail.</span></span> <span data-ttu-id="25492-149">Une classe de base abstraite vous permet d’ajouter une implémentation virtuelle par défaut.</span><span class="sxs-lookup"><span data-stu-id="25492-149">An abstract base class allows you to add a default virtual implementation.</span></span>

<span data-ttu-id="25492-150">✔️ envisagez de placer le <xref:System.ObsoleteAttribute> sur les types et les membres que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="25492-150">✔️ CONSIDER placing the <xref:System.ObsoleteAttribute> on types and members that you intend to remove.</span></span> <span data-ttu-id="25492-151">L’attribut doit comporter des instructions pour la mise à jour du code afin de ne plus utiliser l’API obsolète.</span><span class="sxs-lookup"><span data-stu-id="25492-151">The attribute should have instructions for updating code to no longer use the obsolete API.</span></span>

> <span data-ttu-id="25492-152">Le code qui appelle des types et méthodes avec le <xref:System.ObsoleteAttribute> génère un avertissement de génération avec le message fourni à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="25492-152">Code that calls types and methods with the <xref:System.ObsoleteAttribute> will generate a build warning with the message supplied to the attribute.</span></span> <span data-ttu-id="25492-153">Les avertissements donnent aux personnes qui utilisent la surface d’API obsolète le temps de migrer afin que la plupart ne l’utilisent plus quand elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="25492-153">The warnings give people who use the obsolete API surface time to migrate so that when the obsolete API is removed, most are no longer using it.</span></span>

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

<span data-ttu-id="25492-154">✔️ envisagez de conserver indéfiniment les types et les méthodes avec le <xref:System.ObsoleteAttribute> dans les bibliothèques de niveau faible et intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="25492-154">✔️ CONSIDER keeping types and methods with the <xref:System.ObsoleteAttribute> indefinitely in low and middle-level libraries.</span></span>

> <span data-ttu-id="25492-155">La suppression des API est un changement cassant binaire.</span><span class="sxs-lookup"><span data-stu-id="25492-155">Removing APIs is a binary breaking change.</span></span> <span data-ttu-id="25492-156">Envisagez de conserver les méthodes et types obsolètes si leur mise à jour présente un faible coût et n’ajoute pas beaucoup de dette technique à votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="25492-156">Considering keeping obsolete types and methods if maintaining them is low cost and doesn't add lot of technical debt to your library.</span></span> <span data-ttu-id="25492-157">Le fait de ne pas supprimer les types et méthodes peut permettre d’éviter les pires scénarios mentionnés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="25492-157">Not removing types and methods can help avoid the worst-case scenarios mentioned above.</span></span>

## <a name="see-also"></a><span data-ttu-id="25492-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25492-158">See also</span></span>

- [<span data-ttu-id="25492-159">Considérations relatives à la version et la mise à jour pour les développeurs C#</span><span class="sxs-lookup"><span data-stu-id="25492-159">Version and update considerations for C# developers</span></span>](../../csharp/whats-new/version-update-considerations.md)
- [<span data-ttu-id="25492-160">A definitive guide to API-breaking changes in .NET</span><span class="sxs-lookup"><span data-stu-id="25492-160">A definitive guide to API-breaking changes in .NET</span></span>](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [<span data-ttu-id="25492-161">Règles de modification avec rupture .NET</span><span class="sxs-lookup"><span data-stu-id="25492-161">.NET breaking change rules</span></span>](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="25492-162">Précédent</span><span class="sxs-lookup"><span data-stu-id="25492-162">Previous</span></span>](versioning.md)
