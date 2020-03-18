---
title: Algorithme de chargement d’assemblage satellite - .NET Core
description: Description des détails de l’algorithme de chargement d’assemblage par satellite dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70234634"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algorithme de chargement d’assemblage par satellite

Les assemblages satellitaires sont utilisés pour stocker des ressources localisées personnalisées pour la langue et la culture.

Les assemblages de satellites utilisent un algorithme de chargement différent de celui des assemblages gérés en général.

## <a name="when-are-satellite-assemblies-loaded"></a>Quand les assemblages satellites sont-ils chargés?

Les assemblages satellitaires sont chargés lors du chargement d’une ressource localisée.

L’API de base pour <xref:System.Resources.ResourceManager?displayProperty=fullName> charger les ressources localisées est la classe. En <xref:System.Resources.ResourceManager> fin de <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> compte, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>la classe appellera la méthode pour chacun .

Les API de niveau supérieur peuvent extraire l’API de bas niveau.

## <a name="algorithm"></a>Algorithm

Le processus de secours pour les ressources .NET Core comprend les étapes suivantes :

1. Déterminez `active` <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance. Dans tous les `active` cas, l’exemple <xref:System.Runtime.Loader.AssemblyLoadContext>est celui de l’assemblée d’exécution .

2. L’instance `active` tente de charger un assemblage satellite pour la culture demandée dans l’ordre prioritaire par :
    - Vérification de son cache.
    - Vérification de l’annuaire de l’assemblage actuellement exécutant pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> une `es-MX`sous-direction qui correspond à la demande (par exemple ).

        > [!NOTE]
        > Cette fonctionnalité n’a pas été implémentée dans .NET Core avant 3.0.
        >
        > [!NOTE]
        > Sur Linux et macOS, la sous-direction est sensible aux cas et doit soit:
        > - Exactement cas de match.
        > - Soyez dans le cas inférieur.

    - Si `active` c’est le <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> cas, en exécutant la logique [d’analyse par satellite par défaut (ressource).](default-probing.md#satellite-resource-assembly-probing)

    - Appel <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> de la fonction.

    - Élever <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement.

    - Élever <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.

3. Si un assemblage satellite est chargé :
   - L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.
   - L’assemblage est recherché pour la ressource demandée. Si le temps d’exécution trouve la ressource dans l’assemblage, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

    > [!NOTE]
    > Pour trouver une ressource dans l’assembly satellite, le runtime recherche le fichier de ressources demandé par <xref:System.Resources.ResourceManager> pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. Dans le fichier des ressources, il recherche le nom de ressource demandé. En cas d’échec, la ressource est traitée comme introuvable.

4. Le temps d’exécution recherche ensuite les assemblées de la culture des parents à travers de nombreux niveaux potentiels, chaque fois répéter les étapes 2 & 3.

    Chaque culture n’a qu’un <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> seul parent, qui est défini par la propriété.

    La recherche de cultures parentales <xref:System.Globalization.CultureInfo.Parent%2A> s’arrête lorsque la propriété d’une culture est <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.

    Pour <xref:System.Globalization.CultureInfo.InvariantCulture>le , nous ne revenons pas aux étapes 2 & 3, mais plutôt continuer avec l’étape 5.

5. Si la ressource n’est toujours pas trouvée, la ressource pour la culture par défaut (repli) est utilisée.

   En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal. Toutefois, vous <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pouvez <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> spécifier pour la propriété. Cette valeur indique que l’emplacement de repli ultime pour les ressources est un assemblage satellite plutôt que l’assemblage principal.

    > [!NOTE]
    > La culture par défaut est le repli ultime. Par conséquent, nous vous recommandons d’inclure toujours un ensemble exhaustif de ressources dans le fichier des ressources par défaut. Vous empêchez ainsi la levée d’exceptions. En ayant un ensemble exhaustif, vous fournissez un repli pour toutes les ressources et assurez-vous qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas culturellement spécifique.

6. Enfin,
   - Si le temps d’exécution ne trouve pas de fichier de <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> ressources pour une culture par défaut (repli), une ou une exception est lancée.
   - Si le fichier de ressources est trouvé mais que `null`la ressource demandée n’est pas présente, la demande revient .
