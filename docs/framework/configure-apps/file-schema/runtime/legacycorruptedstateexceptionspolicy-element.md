---
title: Élément <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6191ee2169a85725f0367763874e60c0ceb1d7a4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489434"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy> Element
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
|`enabled`|Attribut requis.<br /><br /> Spécifie que l’application interceptera endommager des échecs d’état d’exception telles que des violations d’accès.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|L’application n’intercepte pas endommager les échecs d’état d’exception telles que des violations d’accès. Il s'agit de la valeur par défaut.|  
|`true`|L’application interceptera endommager des échecs d’état d’exception telles que des violations d’accès.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Dans le .NET Framework version 3.5 et versions antérieure, le common language runtime autorise le code managé intercepter les exceptions qui ont été générées par les États de processus endommagé. Une violation d’accès est un exemple de ce type d’exception.  
  
 À compter de .NET Framework 4, le code managé n’intercepte plus ces types d’exceptions dans `catch` blocs. Toutefois, vous pouvez remplacer cette modification et maintenir la gestion des exceptions d’état endommagé de deux manières :  
  
- Définir le `<legacyCorruptedStateExceptionsPolicy>` l’élément `enabled` attribut `true`. Ce paramètre de configuration est appliquée au niveau du processus et affecte toutes les méthodes.  
  
 ou  
  
- Appliquer le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> d’attribut à la méthode qui contient les exceptions `catch` bloc.  
  
 Cet élément de configuration est disponible uniquement dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le .NET Framework 4 et intercepter des échecs d’exception altérer tout état.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
