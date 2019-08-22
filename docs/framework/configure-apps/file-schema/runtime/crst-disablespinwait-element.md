---
title: < élément Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663839"
---
# <a name="crst_disablespinwait-element"></a>\<Crst_DisableSpinWait >, élément

Spécifie s’il faut désactiver l’attente de spin pour une section critique en cas de conflit.  
  
 \<configuration>  
\<runtime>  
\<Crst_DisableSpinWait>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**enabled**|Spécifie si la rotation en attente des sections critiques lorsqu’elles sont confrontées est désactivée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|1|Désactivez l’attente de spin quand une section critique ne peut pas être acquise.|  
|0|Ne désactivez pas l’attente de spin quand une section critique ne peut pas être acquise. Valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les différents paramètres de configuration du Runtime.|  
  
## <a name="example"></a>Exemples  

L’exemple suivant désactive l’attente de spin-Wait dans les sections critiques en cas de conflit.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
