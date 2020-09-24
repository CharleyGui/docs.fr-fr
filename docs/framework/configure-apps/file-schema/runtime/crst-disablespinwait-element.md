---
title: Élément <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 45052d99bb297ac39d058fa405fe57a7c991f738
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151348"
---
# <a name="crst_disablespinwait-element"></a>\<Crst_DisableSpinWait> (élément)

Spécifie s’il faut désactiver l’attente de spin pour une section critique en cas de conflit.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**activé**|Spécifie si la rotation en attente des sections critiques lorsqu’elles sont confrontées est désactivée.|  
  
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
  
## <a name="example"></a>Exemple  

L’exemple suivant désactive l’attente de spin-Wait dans les sections critiques en cas de conflit.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
