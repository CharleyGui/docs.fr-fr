---
title: Indicateurs de fonctionnalités
description: Implémenter des indicateurs de fonctionnalités dans les applications natives du Cloud en tirant parti de la configuration de Azure App
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: ee45c9f187b056887ea6dd3a08da508afca51987
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158095"
---
# <a name="feature-flags"></a><span data-ttu-id="abf06-103">Indicateurs de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="abf06-103">Feature flags</span></span>

<span data-ttu-id="abf06-104">Dans le chapitre 1, nous avons affirmé que le Cloud native est bien plus rapide que la vitesse et l’agilité.</span><span class="sxs-lookup"><span data-stu-id="abf06-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="abf06-105">Les utilisateurs attendent une réactivité rapide, des fonctionnalités novatrices et des temps d’arrêt nuls.</span><span class="sxs-lookup"><span data-stu-id="abf06-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="abf06-106">`Feature flags` est une technique de déploiement moderne qui permet d’accroître l’agilité des applications Cloud natives.</span><span class="sxs-lookup"><span data-stu-id="abf06-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="abf06-107">Elles vous permettent de déployer de nouvelles fonctionnalités dans un environnement de production, mais de limiter leur disponibilité.</span><span class="sxs-lookup"><span data-stu-id="abf06-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="abf06-108">Avec le raccourci d’un commutateur, vous pouvez activer une nouvelle fonctionnalité pour des utilisateurs spécifiques sans redémarrer l’application ou déployer un nouveau code.</span><span class="sxs-lookup"><span data-stu-id="abf06-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="abf06-109">Ils séparent la publication de nouvelles fonctionnalités du déploiement de code.</span><span class="sxs-lookup"><span data-stu-id="abf06-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="abf06-110">Les indicateurs de fonctionnalités sont basés sur la logique conditionnelle qui contrôlent la visibilité des fonctionnalités pour les utilisateurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="abf06-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="abf06-111">Dans les systèmes modernes Cloud natifs, il est courant de déployer de nouvelles fonctionnalités en production tôt, mais de les tester avec un public limité.</span><span class="sxs-lookup"><span data-stu-id="abf06-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="abf06-112">À mesure que la confiance augmente, la fonctionnalité peut être déployée de manière incrémentielle pour un public plus étendu.</span><span class="sxs-lookup"><span data-stu-id="abf06-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="abf06-113">Voici d’autres cas d’usage pour les indicateurs de fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="abf06-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="abf06-114">Limitez les fonctionnalités Premium à des groupes de clients spécifiques prêts à payer des frais d’abonnement plus élevés.</span><span class="sxs-lookup"><span data-stu-id="abf06-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="abf06-115">Stabiliser un système en désactivant rapidement un problème, en évitant les risques liés à une restauration ou à un correctif immédiat.</span><span class="sxs-lookup"><span data-stu-id="abf06-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="abf06-116">Désactivez une fonctionnalité facultative avec une consommation élevée de ressources pendant les périodes d’utilisation maximale.</span><span class="sxs-lookup"><span data-stu-id="abf06-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="abf06-117">Procédez `experimental feature releases` à des petits segments utilisateur pour valider la faisabilité et la popularité.</span><span class="sxs-lookup"><span data-stu-id="abf06-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="abf06-118">Les indicateurs de fonctionnalité favorisent également le `trunk-based` développement.</span><span class="sxs-lookup"><span data-stu-id="abf06-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="abf06-119">Il s’agit d’un modèle de branchement de contrôle de code source dans lequel les développeurs collaborent sur les fonctionnalités d’une seule et même branche.</span><span class="sxs-lookup"><span data-stu-id="abf06-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="abf06-120">L’approche minimise les risques et la complexité liés à la fusion d’un grand nombre de branches de fonctionnalités longues.</span><span class="sxs-lookup"><span data-stu-id="abf06-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="abf06-121">Les fonctionnalités ne sont pas disponibles tant qu’elles ne sont pas activées.</span><span class="sxs-lookup"><span data-stu-id="abf06-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="abf06-122">Implémentation d’indicateurs de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="abf06-122">Implementing feature flags</span></span>

<span data-ttu-id="abf06-123">À son cœur, un indicateur de fonctionnalité est une référence à un simple `decision object` .</span><span class="sxs-lookup"><span data-stu-id="abf06-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="abf06-124">Elle retourne un état booléen de `on` ou `off` .</span><span class="sxs-lookup"><span data-stu-id="abf06-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="abf06-125">L’indicateur encapsule généralement un bloc de code qui encapsule une fonctionnalité de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="abf06-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="abf06-126">L’état de l’indicateur détermine si ce bloc de code s’exécute pour un utilisateur donné.</span><span class="sxs-lookup"><span data-stu-id="abf06-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="abf06-127">La figure 10-11 illustre l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="abf06-127">Figure 10-11 shows the implementation.</span></span>

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="abf06-128">**Figure 10-11** -implémentation d’indicateur de fonctionnalité simple.</span><span class="sxs-lookup"><span data-stu-id="abf06-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="abf06-129">Notez comment cette approche sépare la logique de décision du code de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="abf06-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="abf06-130">Dans le chapitre 1, nous avons abordé le `Twelve-Factor App` .</span><span class="sxs-lookup"><span data-stu-id="abf06-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="abf06-131">L’aide recommandée pour conserver les paramètres de configuration externes du code exécutable de l’application.</span><span class="sxs-lookup"><span data-stu-id="abf06-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="abf06-132">Si nécessaire, les paramètres peuvent être lus à partir de la source externe.</span><span class="sxs-lookup"><span data-stu-id="abf06-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="abf06-133">Les valeurs de configuration de l’indicateur de fonctionnalité doivent également être indépendantes de leur code base.</span><span class="sxs-lookup"><span data-stu-id="abf06-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="abf06-134">En externalant la configuration de l’indicateur dans un dépôt distinct, vous pouvez modifier l’état de l’indicateur sans modifier et redéployer l’application.</span><span class="sxs-lookup"><span data-stu-id="abf06-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="abf06-135">[Azure App configuration](/azure/azure-app-configuration/overview) fournit un référentiel centralisé pour les indicateurs de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="abf06-135">[Azure App Configuration](/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="abf06-136">Il vous permet de définir différents types d’indicateurs de fonctionnalités et de manipuler leurs États rapidement et en toute confiance.</span><span class="sxs-lookup"><span data-stu-id="abf06-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="abf06-137">Vous ajoutez les bibliothèques clientes de configuration d’application à votre application pour activer la fonctionnalité d’indicateur de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="abf06-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="abf06-138">Différents frameworks de langage de programmation sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="abf06-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="abf06-139">Les indicateurs de fonctionnalités peuvent être facilement implémentés dans un [service ASP.net Core](/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="abf06-139">Feature flags can be easily implemented in an [ASP.NET Core service](/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="abf06-140">L’installation des bibliothèques de gestion des fonctionnalités .NET et du fournisseur de configuration d’application vous permet d’ajouter des indicateurs de fonctionnalités de façon déclarative à votre code.</span><span class="sxs-lookup"><span data-stu-id="abf06-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="abf06-141">Ils activent les `FeatureGate` attributs afin que vous n’ayez pas à écrire manuellement les instructions if dans votre code base.</span><span class="sxs-lookup"><span data-stu-id="abf06-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="abf06-142">Une fois configuré dans votre classe de démarrage, vous pouvez ajouter la fonctionnalité d’indicateur de fonctionnalité au niveau du contrôleur, de l’action ou de l’intergiciel (middleware).</span><span class="sxs-lookup"><span data-stu-id="abf06-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="abf06-143">La figure 10-12 illustre l’implémentation du contrôleur et de l’action :</span><span class="sxs-lookup"><span data-stu-id="abf06-143">Figure 10-12 presents controller and action implementation:</span></span>

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="abf06-144">**Figure 10-12** : implémentation de l’indicateur de fonctionnalité dans un contrôleur et une action.</span><span class="sxs-lookup"><span data-stu-id="abf06-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="abf06-145">Si un indicateur de fonctionnalité est désactivé, l’utilisateur recevra un code d’État 404 (introuvable) sans corps de réponse.</span><span class="sxs-lookup"><span data-stu-id="abf06-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="abf06-146">Les indicateurs de fonctionnalités peuvent également être injectés directement dans des classes C#.</span><span class="sxs-lookup"><span data-stu-id="abf06-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="abf06-147">La figure 10-13 illustre l’injection d’indicateurs de fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="abf06-147">Figure 10-13 shows feature flag injection:</span></span>

```csharp
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="abf06-148">**Figure 10-13** : insertion d’un indicateur de fonctionnalité dans une classe.</span><span class="sxs-lookup"><span data-stu-id="abf06-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="abf06-149">Les bibliothèques de gestion des fonctionnalités gèrent le cycle de vie des indicateurs de fonctionnalités en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="abf06-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="abf06-150">Par exemple, pour réduire le nombre élevé d’appels au magasin de configurations, les bibliothèques cachent les États d’indicateur pour une durée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="abf06-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="abf06-151">Elles peuvent garantir l’immuabilité des États d’indicateur pendant un appel de requête.</span><span class="sxs-lookup"><span data-stu-id="abf06-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="abf06-152">Ils proposent également un `Point-in-time snapshot` .</span><span class="sxs-lookup"><span data-stu-id="abf06-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="abf06-153">Vous pouvez reconstruire l’historique de n’importe quelle valeur de clé et fournir sa valeur passée à tout moment dans les sept jours précédents.</span><span class="sxs-lookup"><span data-stu-id="abf06-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="abf06-154">[Précédent](devops.md) 
> [Suivant](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="abf06-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>
