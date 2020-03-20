---
title: Élément <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153904"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Element
Optimise la sonde pour les assemblys satellites.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
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
|`enabled`|Attribut requis.<br /><br /> Précise si le temps d’exécution de langage commun optimise la sonde pour les assemblages satellites.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le temps d’exécution n’optimise pas la sonde pour les assemblages de satellites. Il s’agit de la valeur par défaut.|  
|`true`|Le temps d’exécution optimise la sonde pour les assemblages de satellites.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes   
 En général, le gestionnaire des ressources sonde les ressources, comme le documente le sujet [des ressources d’emballage et de déploiement.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) Cela signifie que lorsque Resource Manager sonde pour une version localisée particulière d’une ressource, il peut regarder dans le cache d’assemblage global, regarder dans <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> un dossier spécifique à la culture dans la base de code de l’application, interroger Windows Installer pour les assemblages de satellites, et élever l’événement. L’élément `<relativeBindForResources>` optimise la façon dont le gestionnaire des ressources sonde les assemblages de satellites. Il peut améliorer les performances lors de l’examen des ressources dans les conditions suivantes :  
  
- Lorsque l’assemblage satellite est déployé au même endroit que l’assemblage du code. En d’autres termes, si l’assemblage de code est installé dans le cache d’assemblage global, les assemblages satellites doivent également y être installés. Si l’assemblage de code est installé dans la base de code de l’application, les assemblages satellites doivent également être installés dans un dossier spécifique à la culture dans la base de code.  
  
- Lorsque Windows Install n’est pas utilisé ou n’est utilisé que rarement pour l’installation à la demande d’assemblages satellites.  
  
- Lorsque le code d’application ne gère pas l’événement. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
  
 Définir `enabled` l’attribut `<relativeBindForResources>` de `true` l’élément pour optimiser la sonde de Resource Manager pour les assemblages satellitaires comme suit :  
  
- Il utilise l’emplacement de l’assemblage de code parent pour sonder l’assemblage du satellite.  
  
- Il ne demande pas Windows Install pour les assemblages de satellites.  
  
- Il ne soulève <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pas l’événement.  
  
## <a name="see-also"></a>Voir aussi

- [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
