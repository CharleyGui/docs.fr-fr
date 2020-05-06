---
title: Algorithme de chargement d’assembly satellite-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly satellite dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 17f29a9aca79019daa91736e586bf1b6b753a9ec
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859531"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algorithme de chargement d’assembly satellite

Les assemblys satellites sont utilisés pour stocker les ressources localisées personnalisées pour la langue et la culture.

Les assemblys satellites utilisent un algorithme de chargement différent des assemblys managés généraux.

## <a name="when-are-satellite-assemblies-loaded"></a>Quand les assemblys satellites sont-ils chargés ?

Les assemblys satellites sont chargés lors du chargement d’une ressource localisée.

L’API de base pour charger des ressources localisées <xref:System.Resources.ResourceManager?displayProperty=fullName> est la classe. Finalement, <xref:System.Resources.ResourceManager> la classe appellera la <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> méthode pour chaque <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.

Les API de niveau supérieur peuvent faire abstraction de l’API de bas niveau.

## <a name="algorithm"></a>Algorithm

Le processus de secours pour les ressources .NET Core comprend les étapes suivantes :

1. Déterminez `active` <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance. Dans tous les cas, `active` l’instance est le de l’assembly en cours d' <xref:System.Runtime.Loader.AssemblyLoadContext>exécution.

2. L' `active` instance tente de charger un assembly satellite pour la culture demandée par ordre de priorité en procédant comme suit :
    - Vérification de son cache.
    - Vérification du répertoire de l’assembly en cours d’exécution pour un sous-répertoire qui correspond <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> au demandé ( `es-MX`par exemple).

        > [!NOTE]
        > Cette fonctionnalité n’a pas été implémentée dans .NET Core avant 3,0.
        >
        > [!NOTE]
        > Sur Linux et macOS, le sous-répertoire est sensible à la casse et doit être :
        >
        > - Respecter exactement la casse.
        > - Être en minuscules.

    - Si `active` est l' <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance de, en exécutant la logique de sondage de l' [assembly satellite (ressource) par défaut](default-probing.md#satellite-resource-assembly-probing) .

    - Appel de <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> la fonction.

    - Déclenchement de <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement.

    - Déclenchement de <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.

3. Si un assembly satellite est chargé :
   - L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.
   - La ressource demandée est recherchée dans l’assembly. Si le runtime trouve la ressource dans l’assembly, il l’utilise. S’il ne trouve pas la ressource, il continue la recherche.

    > [!NOTE]
    > Pour trouver une ressource dans l’assembly satellite, le runtime recherche le fichier de ressources demandé par <xref:System.Resources.ResourceManager> pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. Dans le fichier de ressources, il recherche le nom de ressource demandé. En cas d’échec, la ressource est traitée comme introuvable.

4. Le Runtime effectue ensuite une recherche dans les assemblys de culture parents par le biais de nombreux niveaux potentiels, en répétant les étapes 2 & 3.

    Chaque culture n’a qu’un seul parent, qui est défini <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> par la propriété.

    La recherche de cultures parentes s’arrête quand la <xref:System.Globalization.CultureInfo.Parent%2A> propriété d' <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>une culture est.

    Pour le <xref:System.Globalization.CultureInfo.InvariantCulture>, nous ne revenons pas aux étapes 2 & 3, mais nous continuons à l’étape 5.

5. Si la ressource est toujours introuvable, la ressource de la culture par défaut (de secours) est utilisée.

   En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal. Toutefois, vous pouvez spécifier <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pour la <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> propriété. Cette valeur indique que l’emplacement de secours ultime pour les ressources est un assembly satellite plutôt que l’assembly principal.

    > [!NOTE]
    > La culture par défaut est le secours ultime. Par conséquent, nous vous recommandons de toujours inclure un ensemble exhaustif de ressources dans le fichier de ressources par défaut. Vous empêchez ainsi la levée d’exceptions. En ayant un ensemble exhaustif, vous fournissez une solution de secours pour toutes les ressources et vous vous assurez qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas spécifique à la culture.

6. Enfin,
   - Si le runtime ne trouve pas de fichier de ressources pour une culture par défaut (de <xref:System.Resources.MissingManifestResourceException> secours <xref:System.Resources.MissingSatelliteAssemblyException> ), une exception ou est levée.
   - Si le fichier de ressources est trouvé mais que la ressource demandée n’est pas présente `null`, la demande est retournée.
