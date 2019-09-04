---
title: Élément <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb198d6a19e25df4c86186d35aab3330c53121c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252764"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames>, élément
Spécifie s’il faut ignorer la validation des noms forts sur les assemblys de confiance totale qui sont chargés dans un <xref:System.AppDomain>niveau de confiance totale.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si la fonctionnalité de contournement qui évite de valider des noms forts pour les assemblys de confiance totale est activée. Lorsque cette fonctionnalité est activée, les noms forts ne sont pas validés pour être corrects lorsque l’assembly est chargé. Par défaut, il s’agit de `true`.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans <xref:System.AppDomain>un niveau de confiance totale. Il s'agit de la valeur par défaut.|  
|`false`|Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un <xref:System.AppDomain>niveau de confiance totale. La signature de nom fort est vérifiée uniquement pour l’exactitude de la signature ; elle n’est pas comparée à un autre nom fort pour une correspondance.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 La fonctionnalité de contournement de nom fort évite la surcharge liée à la vérification de signature de nom fort des assemblys de confiance totale.  
  
 Cette fonctionnalité s'applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :  
  
- Confiance totale sans <xref:System.Security.Policy.StrongName> preuve (par exemple, a `MyComputer` une preuve de zone).  
  
- Chargé dans un <xref:System.AppDomain> de confiance totale.  
  
- Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.  
  
- Sans signature différée.  
  
> [!NOTE]
> Si la fonctionnalité de contournement a été désactivée pour toutes les applications sur l’ordinateur à l’aide d’une clé de Registre, ce paramètre de fichier de configuration n’a aucun effet. Pour plus d'informations, voir [Procédure : Désactiver la fonctionnalité consistant à ignorer les noms forts](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier le comportement qui valide la signature de nom fort sur les assemblys de confiance totale.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Guide pratique pour désactiver la fonctionnalité consistant à ignorer les noms forts](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
