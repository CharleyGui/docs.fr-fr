---
title: Clichés instantanés d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
ms.openlocfilehash: 9fc8a4aeeeca40f71ed9114a9db40b9a56e5fe6b
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204570"
---
# <a name="shadow-copying-assemblies"></a>Clichés instantanés d'assemblys

Les clichés instantanés permettent aux assemblys qui sont utilisés dans un domaine d'application d'être mis à jour sans décharger le domaine d'application. Ceci est particulièrement utile pour les applications qui doivent être disponibles en permanence, comme des sites ASP.NET.

> [!IMPORTANT]
> Les clichés instantanés ne sont pas pris en charge dans les applications du Windows 8. x Store.

Le common language runtime verrouille un fichier d'assembly quand l'assembly est chargé, de sorte que le fichier ne peut pas être mis à jour jusqu'à ce que l'assembly soit déchargé. La seule façon de décharger un assembly d'un domaine d'application est de décharger le domaine d'application. Donc, dans des circonstances normales, un assembly ne peut pas être mis à jour sur le disque tant que tous les domaines d'application qui l'utilisent n'ont pas été déchargés.

Quand un domaine d'application est configuré pour effectuer un cliché instantané des fichiers, les assemblys du chemin d'accès de l'application sont copiés vers un autre emplacement et chargés à partir de cet emplacement. La copie est verrouillée, mais le fichier d'assembly d'origine est déverrouillé et peut être mis à jour.

> [!IMPORTANT]
> Les seuls assemblys qui peuvent faire l'objet de clichés instantanés sont ceux qui sont stockés dans le répertoire de l'application ou dans ses sous-répertoires, spécifiés par les propriétés <xref:System.AppDomainSetup.ApplicationBase%2A> et <xref:System.AppDomainSetup.PrivateBinPath%2A> quand le domaine d'application est configuré. Les assemblys stockés dans le Global Assembly Cache ne sont pas l'objet de clichés instantanés.

Cet article contient les sections suivantes :

- [Activation et utilisation des clichés instantanés](#EnablingAndUsing) décrit l’utilisation de base et les options disponibles pour les clichés instantanés.

- [Performances du démarrage](#StartupPerformance) décrit les changements apportés aux clichés instantanés dans .NET Framework 4 pour améliorer les performances du démarrage, et comment rétablir le comportement des versions antérieures.

- [Méthodes obsolètes](#ObsoleteMethods) décrit les changements apportés aux propriétés et aux méthodes qui contrôlent les clichés instantanés dans .NET Framework 2.0.

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a>Activation et utilisation des clichés instantanés

Vous pouvez utiliser les propriétés de la classe <xref:System.AppDomainSetup> comme suit pour configurer un domaine d'application pour les clichés instantanés :

- Activez les clichés instantanés en définissant la propriété <xref:System.AppDomainSetup.ShadowCopyFiles%2A> à la valeur de chaîne `"true"`.

  Par défaut, cette valeur fait que tous les assemblys dans le chemin d'accès de l'application sont copiés vers un cache de téléchargement avant leur chargement. Il s'agit du même cache que celui qui est géré par le common language runtime pour stocker les fichiers téléchargés à partir d'autres ordinateurs. Le common language runtime supprime automatiquement les fichiers quand ils ne sont plus nécessaires.

- Vous pouvez aussi définir un emplacement personnalisé pour les fichiers des clichés instantanés en utilisant les propriétés <xref:System.AppDomainSetup.CachePath%2A> et <xref:System.AppDomainSetup.ApplicationName%2A>.

  Le chemin d'accès de base de l'emplacement est formé en concaténant la propriété <xref:System.AppDomainSetup.ApplicationName%2A> et la propriété <xref:System.AppDomainSetup.CachePath%2A> comme sous-répertoire. Les clichés instantanés des assemblys sont copiés vers des sous-répertoires de ce chemin d'accès, et non pas dans le chemin d'accès de base lui-même.

  > [!NOTE]
  > Si la propriété <xref:System.AppDomainSetup.ApplicationName%2A> n'est pas définie, la propriété <xref:System.AppDomainSetup.CachePath%2A> est ignorée et le cache de téléchargement est utilisé. Aucune exception n'est levée.

  Si vous spécifiez un emplacement personnalisé, vous devez vous charger de nettoyer les répertoires et les fichiers copiés quand ils ne sont plus nécessaires. Ils ne sont pas supprimés automatiquement.

  Il existe plusieurs raisons pour lesquelles vous voudrez peut-être définir un emplacement personnalisé pour les fichiers de clichés instantanés. Vous pouvez souhaiter définir un emplacement personnalisé pour les fichiers de clichés instantanés si votre application génère un grand nombre de copies. Le cache de téléchargement est limité en taille, pas quant à la durée de vie : il est donc possible que le common language runtime tente de supprimer un fichier qui est toujours en cours d'utilisation. Une autre raison pour définir un emplacement personnalisé est quand des utilisateurs exécutant votre application n'ont pas d'accès en écriture à l'emplacement du répertoire utilisé par common language runtime pour le cache de téléchargement.

- Limitez éventuellement les assemblys qui font l'objet de clichés instantanés en utilisant la propriété <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>.

  Quand vous activez les clichés instantanés pour un domaine d'application, le comportement par défaut est de copier tous les assemblys dans le chemin d'accès de l'application, c'est-à-dire dans les répertoires spécifiés par les propriétés <xref:System.AppDomainSetup.ApplicationBase%2A> et <xref:System.AppDomainSetup.PrivateBinPath%2A>. Vous pouvez limiter la copie vers les répertoires sélectionnés en créant une chaîne qui contient seulement les répertoires pour lesquels vous voulez effectuer des clichés instantanés, et en l'affectant à la propriété <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>. Séparez les répertoires par des points-virgules. Les seuls assemblys qui font l'objet de clichés instantanés sont alors ceux des répertoires sélectionnés.

  > [!NOTE]
  > Si vous n'affectez pas une chaîne à la propriété <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> ou si vous définissez cette propriété à `null`, tous les assemblys dans les répertoires spécifiés par les propriétés <xref:System.AppDomainSetup.ApplicationBase%2A> et <xref:System.AppDomainSetup.PrivateBinPath%2A> font l'objet d'un cliché instantané.

  > [!IMPORTANT]
  > Les chemins d'accès des répertoires ne doivent pas contenir de points-virgules, car le point-virgule est le caractère délimiteur. Il n'existe pas de caractère d'échappement pour les points-virgules.

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a>Performances du démarrage

Quand un domaine d'application qui utilise des clichés instantanés démarre, un certain délai est nécessaire pour que les assemblys du répertoire de l'application soient copiés dans le répertoire des clichés instantanés, ou pour qu'ils soient vérifiés s'ils se trouvent déjà à cet emplacement. Avant .NET Framework 4, tous les assemblys étaient copiés dans un répertoire temporaire. Chaque assembly était ouvert pour vérifier le nom de l'assembly et le nom fort était validé. Chaque assembly était vérifié pour voir s'il avait été mis à jour plus récemment que la copie du répertoire des clichés instantanés. Le cas échéant, il était copié dans le répertoire des clichés instantanés. Enfin, les copies temporaires étaient effacées.

Depuis .NET Framework 4, le comportement par défaut au démarrage est de comparer directement la date et l’heure du fichier de chaque assembly du répertoire de l’application à la date et l’heure du fichier de la copie du répertoire des clichés instantanés. Si l’assembly a été mis à jour, il est copié selon la même procédure que dans les versions antérieures du .NET Framework ; dans le cas contraire, la copie du répertoire des clichés instantanés est chargée.

L'amélioration des performances qui en résulte est plus importante pour les applications dans lesquelles les assemblys ne changent pas souvent et où les modifications se produisent généralement dans un petit sous-ensemble d'assemblys. Si une majorité des assemblys d'une application sont fréquemment modifiés, le nouveau comportement par défaut peut provoquer une régression des performances. Vous pouvez restaurer le comportement de démarrage des versions précédentes du .NET Framework en ajoutant l' [ \<élément shadowCopyVerifyByTimestamp>](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) au fichier de configuration, avec `enabled="false"`.

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a>Méthodes obsolètes

La classe <xref:System.AppDomain> a plusieurs méthodes, comme <xref:System.AppDomain.SetShadowCopyFiles%2A> et <xref:System.AppDomain.ClearShadowCopyPath%2A>, qui peuvent être utilisées pour contrôler les clichés instantanés sur un domaine d'application, mais celles-ci ont été marquées comme étant obsolètes dans le .NET Framework version 2.0. La méthode recommandée pour configurer un domaine d'application pour les clichés instantanés est d'utiliser les propriétés de la classe <xref:System.AppDomainSetup>.

## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<shadowCopyVerifyByTimestamp>, élément](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
