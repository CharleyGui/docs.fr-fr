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
# <a name="feature-flags"></a>Indicateurs de fonctionnalités

Dans le chapitre 1, nous avons affirmé que le Cloud native est bien plus rapide que la vitesse et l’agilité. Les utilisateurs attendent une réactivité rapide, des fonctionnalités novatrices et des temps d’arrêt nuls. `Feature flags` est une technique de déploiement moderne qui permet d’accroître l’agilité des applications Cloud natives. Elles vous permettent de déployer de nouvelles fonctionnalités dans un environnement de production, mais de limiter leur disponibilité. Avec le raccourci d’un commutateur, vous pouvez activer une nouvelle fonctionnalité pour des utilisateurs spécifiques sans redémarrer l’application ou déployer un nouveau code. Ils séparent la publication de nouvelles fonctionnalités du déploiement de code.

Les indicateurs de fonctionnalités sont basés sur la logique conditionnelle qui contrôlent la visibilité des fonctionnalités pour les utilisateurs au moment de l’exécution. Dans les systèmes modernes Cloud natifs, il est courant de déployer de nouvelles fonctionnalités en production tôt, mais de les tester avec un public limité. À mesure que la confiance augmente, la fonctionnalité peut être déployée de manière incrémentielle pour un public plus étendu.

Voici d’autres cas d’usage pour les indicateurs de fonctionnalités :

- Limitez les fonctionnalités Premium à des groupes de clients spécifiques prêts à payer des frais d’abonnement plus élevés.
- Stabiliser un système en désactivant rapidement un problème, en évitant les risques liés à une restauration ou à un correctif immédiat.
- Désactivez une fonctionnalité facultative avec une consommation élevée de ressources pendant les périodes d’utilisation maximale.
- Procédez `experimental feature releases` à des petits segments utilisateur pour valider la faisabilité et la popularité.

Les indicateurs de fonctionnalité favorisent également le `trunk-based` développement. Il s’agit d’un modèle de branchement de contrôle de code source dans lequel les développeurs collaborent sur les fonctionnalités d’une seule et même branche. L’approche minimise les risques et la complexité liés à la fusion d’un grand nombre de branches de fonctionnalités longues. Les fonctionnalités ne sont pas disponibles tant qu’elles ne sont pas activées.

## <a name="implementing-feature-flags"></a>Implémentation d’indicateurs de fonctionnalités

À son cœur, un indicateur de fonctionnalité est une référence à un simple `decision object` . Elle retourne un état booléen de `on` ou `off` . L’indicateur encapsule généralement un bloc de code qui encapsule une fonctionnalité de fonctionnalité. L’état de l’indicateur détermine si ce bloc de code s’exécute pour un utilisateur donné. La figure 10-11 illustre l’implémentation.

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**Figure 10-11** -implémentation d’indicateur de fonctionnalité simple.

Notez comment cette approche sépare la logique de décision du code de la fonctionnalité.

Dans le chapitre 1, nous avons abordé le `Twelve-Factor App` . L’aide recommandée pour conserver les paramètres de configuration externes du code exécutable de l’application. Si nécessaire, les paramètres peuvent être lus à partir de la source externe. Les valeurs de configuration de l’indicateur de fonctionnalité doivent également être indépendantes de leur code base. En externalant la configuration de l’indicateur dans un dépôt distinct, vous pouvez modifier l’état de l’indicateur sans modifier et redéployer l’application.

[Azure App configuration](/azure/azure-app-configuration/overview) fournit un référentiel centralisé pour les indicateurs de fonctionnalité. Il vous permet de définir différents types d’indicateurs de fonctionnalités et de manipuler leurs États rapidement et en toute confiance. Vous ajoutez les bibliothèques clientes de configuration d’application à votre application pour activer la fonctionnalité d’indicateur de fonctionnalité. Différents frameworks de langage de programmation sont pris en charge.

Les indicateurs de fonctionnalités peuvent être facilement implémentés dans un [service ASP.net Core](/azure/azure-app-configuration/use-feature-flags-dotnet-core). L’installation des bibliothèques de gestion des fonctionnalités .NET et du fournisseur de configuration d’application vous permet d’ajouter des indicateurs de fonctionnalités de façon déclarative à votre code. Ils activent les `FeatureGate` attributs afin que vous n’ayez pas à écrire manuellement les instructions if dans votre code base.

Une fois configuré dans votre classe de démarrage, vous pouvez ajouter la fonctionnalité d’indicateur de fonctionnalité au niveau du contrôleur, de l’action ou de l’intergiciel (middleware). La figure 10-12 illustre l’implémentation du contrôleur et de l’action :

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

**Figure 10-12** : implémentation de l’indicateur de fonctionnalité dans un contrôleur et une action.

Si un indicateur de fonctionnalité est désactivé, l’utilisateur recevra un code d’État 404 (introuvable) sans corps de réponse.

Les indicateurs de fonctionnalités peuvent également être injectés directement dans des classes C#. La figure 10-13 illustre l’injection d’indicateurs de fonctionnalités :

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

**Figure 10-13** : insertion d’un indicateur de fonctionnalité dans une classe.

Les bibliothèques de gestion des fonctionnalités gèrent le cycle de vie des indicateurs de fonctionnalités en arrière-plan. Par exemple, pour réduire le nombre élevé d’appels au magasin de configurations, les bibliothèques cachent les États d’indicateur pour une durée spécifiée. Elles peuvent garantir l’immuabilité des États d’indicateur pendant un appel de requête. Ils proposent également un `Point-in-time snapshot` . Vous pouvez reconstruire l’historique de n’importe quelle valeur de clé et fournir sa valeur passée à tout moment dans les sept jours précédents.

>[!div class="step-by-step"]
>[Précédent](devops.md) 
> [Suivant](infrastructure-as-code.md)
