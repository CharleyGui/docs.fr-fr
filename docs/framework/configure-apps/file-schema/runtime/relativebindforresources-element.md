---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1ac2900707ddb39c62b34b0ebfbc4547cdd2653
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252358"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources >, élément
Optimise la sonde pour les assemblys satellites.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le common language runtime optimise la sonde pour les assemblys satellites.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le runtime n’optimise pas la sonde pour les assemblys satellites. Valeur par défaut.|  
|`true`|Le runtime optimise la sonde pour les assemblys satellites.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 En général, Gestionnaire des ressources sondes pour les ressources, comme indiqué dans la rubrique [empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . Cela signifie que lorsque Gestionnaire des ressources détecte une version localisée particulière d’une ressource, il peut regarder dans le Global Assembly Cache, Rechercher dans un dossier propre à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblys satellites et déclencher l’opération <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement. L' `<relativeBindForResources>` élément optimise la façon dont gestionnaire des ressources sondes pour les assemblys satellites. Elle peut améliorer les performances lors de la détection des ressources dans les conditions suivantes :  
  
- Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code. En d’autres termes, si l’assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés ici. Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier propre à la culture dans la base de code.  
  
- Lorsque Windows Installer n’est pas utilisé ou est rarement utilisé pour l’installation à la demande d’assemblys satellites.  
  
- Lorsque le code d’application ne gère <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pas l’événement.  
  
 La définition `enabled` de l’attribut `<relativeBindForResources>` de l' `true` élément pour optimiser la sonde de gestionnaire des ressources pour les assemblys satellites comme suit :  
  
- Elle utilise l’emplacement de l’assembly de code parent pour détecter l’assembly satellite.  
  
- Il n’interroge pas Windows Installer pour les assemblys satellites.  
  
- Elle ne déclenche pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.  
  
## <a name="see-also"></a>Voir aussi

- [Empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
