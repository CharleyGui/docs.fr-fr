---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2715548a40579375cebbdd5fb9003738a42ff714
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663650"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy >, élément
Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.  
  
 \<configuration>  
\<runtime>  
\<legacyCorruptedStateExceptionsPolicy>  
  
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
  
## <a name="remarks"></a>Notes  
 Dans la .NET Framework version 3,5 et les versions antérieures, le common language runtime permettait au code managé d’intercepter les exceptions levées par des États de processus endommagés. Une violation d’accès est un exemple de ce type d’exception.  
  
 À partir du .NET Framework 4, le code managé n’intercepte plus ces types d' `catch` exceptions dans des blocs. Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières:  
  
- Affectez `<legacyCorruptedStateExceptionsPolicy>` `enabled` à`true`l’attribut de l’élément la valeur. Ce paramètre de configuration est appliqué échelle et affecte toutes les méthodes.  
  
 ou  
  
- Appliquez l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribut à la méthode qui contient le bloc `catch` exceptions.  
  
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
- [Schéma des fichiers de configuration](../index.md)
