---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116456"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>Élément \<legacyCorruptedStateExceptionsPolicy>
Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que l’application intercepte les échecs d’exception d’État, tels que les violations d’accès.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|L’application n’intercepte pas les échecs d’exception d’État endommagés, tels que les violations d’accès. Il s'agit de la valeur par défaut.|  
|`true`|L’application intercepte les échecs d’exception d’État, tels que les violations d’accès.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Dans la .NET Framework version 3,5 et les versions antérieures, le common language runtime permettait au code managé d’intercepter les exceptions levées par des États de processus endommagés. Une violation d’accès est un exemple de ce type d’exception.  
  
 À partir du .NET Framework 4, le code managé n’intercepte plus ces types d’exceptions dans des `catch` blocs. Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières :  
  
- Affectez `<legacyCorruptedStateExceptionsPolicy>` à l’attribut de l’élément la valeur `enabled` `true` . Ce paramètre de configuration est appliqué échelle et affecte toutes les méthodes.  
  
 -ou-  
  
- Appliquez l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribut à la méthode qui contient le `catch` bloc exceptions.  
  
 Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le .NET Framework 4 et intercepter tous les échecs d’exception d’état endommagé.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
