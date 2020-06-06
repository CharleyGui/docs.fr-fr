---
title: Élément <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117628"
---
# <a name="developmentmode-element"></a>Élément \<developmentMode>
Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**developerInstallation**|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>Attribut developerInstallation  
  
|Valeur|Description|  
|-----------|-----------------|  
|**true**|Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
|**false**|Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH. Il s'agit du paramètre par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez ce paramètre uniquement au moment du développement. Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH. Il utilise simplement le premier assembly qu’il trouve.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Procédure : Localiser des assemblys à l’aide de DEVPATH](../../how-to-locate-assemblies-by-using-devpath.md)
