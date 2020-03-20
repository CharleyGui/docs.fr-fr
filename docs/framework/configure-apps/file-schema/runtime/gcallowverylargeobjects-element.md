---
title: Élément <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154125"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects> Element
Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Précise si les tableaux de plus de 2 Go de taille totale sont activés sur des plates-formes 64 bits.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Les tableaux de plus de 2 Go en taille totale ne sont pas activés. Il s’agit de la valeur par défaut.|  
|`true`|Les tableaux de plus de 2 Go de taille totale sont activés sur des plates-formes 64 bits.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes   
 L’utilisation de cet élément dans votre fichier de configuration d’application permet des tableaux de plus de 2 Go de taille, mais ne modifie pas d’autres limites sur la taille de l’objet ou la taille du tableau :  
  
- Le nombre maximum d’éléments <xref:System.UInt32.MaxValue?displayProperty=nameWithType>dans un tableau est .  
  
- L’indice maximal dans une seule dimension est de 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’ethètes et les tableaux de structures uninaires, et de 2 146 435 071 (0X7FEFFFFFFF) pour d’autres types.  
  
- La taille maximale pour les cordes et autres objets non-array est inchangée.  
  
> [!CAUTION]
> Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code dangereux qui suppose que tous les tableaux sont de moins de 2 Go de taille. Par exemple, le code dangereux qui utilise des tableaux comme tampons peut être susceptible de dépassements de tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment activer cette fonctionnalité pour une application.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>Pris en charge dans

.NET Framework 4.5 et versions ultérieures

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
