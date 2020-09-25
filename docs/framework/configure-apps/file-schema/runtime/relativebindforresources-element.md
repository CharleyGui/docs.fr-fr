---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: daf576488e38bed28c7c0e5222bc053659372ff0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183999"
---
# <a name="relativebindforresources-element"></a>Élément \<relativeBindForResources>

Optimise la sonde pour les assemblys satellites.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
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

 En général, Gestionnaire des ressources sondes pour les ressources, comme indiqué dans la rubrique [empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . Cela signifie que lorsque Gestionnaire des ressources détecte une version localisée particulière d’une ressource, il peut regarder dans le Global Assembly Cache, Rechercher dans un dossier propre à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblys satellites et déclencher l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement. L' `<relativeBindForResources>` élément optimise la façon dont gestionnaire des ressources sondes pour les assemblys satellites. Elle peut améliorer les performances lors de la détection des ressources dans les conditions suivantes :  
  
- Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code. En d’autres termes, si l’assembly de code est installé dans le Global Assembly Cache, les assemblys satellites doivent également être installés ici. Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier propre à la culture dans la base de code.  
  
- Lorsque Windows Installer n’est pas utilisé ou est rarement utilisé pour l’installation à la demande d’assemblys satellites.  
  
- Lorsque le code d’application ne gère pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.  
  
 La définition `enabled` de l’attribut de l' `<relativeBindForResources>` élément pour `true` optimiser la sonde de gestionnaire des ressources pour les assemblys satellites comme suit :  
  
- Elle utilise l’emplacement de l’assembly de code parent pour détecter l’assembly satellite.  
  
- Il n’interroge pas Windows Installer pour les assemblys satellites.  
  
- Elle ne déclenche pas l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.  
  
## <a name="see-also"></a>Voir aussi

- [Empaquetage et déploiement de ressources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
