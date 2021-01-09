---
title: gcAllowVeryLargeObjects (élément)
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058127"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects>, élément

Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a>Attributs
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les tableaux dont la taille totale est supérieure à 2 Go sont activés sur les plateformes 64 bits.|  
  
### <a name="enabled-attribute"></a>attribut activé  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Les tableaux d’une taille totale supérieure à 2 Go ne sont pas activés. Il s’agit de la valeur par défaut.|  
|`true`|Les tableaux d’une taille totale supérieure à 2 Go sont activés sur les plateformes 64 bits.|  
  
## <a name="child-elements"></a>Éléments enfants  

Aucun.  
  
## <a name="parent-elements"></a>Éléments parents
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  

 L’utilisation de cet élément dans le fichier de configuration de votre application permet aux tableaux dont la taille est supérieure à 2 Go, mais ne modifie pas les autres limites de taille d’objet ou de taille de tableau :  
  
- Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .  
  
- La taille maximale d’une dimension unique est 2 147 483 591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures sur un octet, et 2 146 435 071 (0X7FEFFFFF) pour les tableaux qui contiennent d’autres types.  
  
- La taille maximale des chaînes et d’autres objets non-tableau est inchangée.  
  
> [!CAUTION]
> Avant d’activer cette fonctionnalité, assurez-vous que votre application n’inclut pas de code non sécurisé qui suppose que la taille de tous les tableaux est inférieure à 2 Go. Par exemple, le code unsafe qui utilise des tableaux comme mémoires tampons peut être vulnérable aux dépassements de mémoire tampon s’il est écrit en supposant que les tableaux ne dépasseront pas 2 Go.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment activer cette fonctionnalité pour une application.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>Pris en charge dans

.NET Framework 4,5 et versions ultérieures

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
