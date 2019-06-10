---
title: Élément <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13dd2f00e08539d2ba502058c74aa4a1525e3ff
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816119"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > élément
Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).  
  
 \<configuration > élément  
\<runtime > élément  
\<enforceFIPSPolicy > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut activer la mise en œuvre d’une exigence de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`true`|Si votre ordinateur est configuré pour exiger des algorithmes de chiffrement à être conforme aux normes FIPS, cette spécification est appliquée. Si une classe implémente un algorithme qui n’est pas conforme à la norme FIPS, les constructeurs ou `Create` méthodes pour cette classe lèvent des exceptions lorsqu’elles sont exécutées sur cet ordinateur. Il s'agit de la valeur par défaut.|  
|`false`|Les algorithmes de chiffrement qui sont utilisés par l’application ne sont pas requis pour être conformes à la norme FIPS, quelle que soit la configuration de l’ordinateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À compter de .NET Framework 2.0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur. Si l’ordinateur est configuré pour exiger des algorithmes pour être conforme à la norme FIPS, et une classe implémente un algorithme qui n’est pas conforme à la norme FIPS, toute tentative pour créer une instance de cette classe lève une exception. Constructeurs lèvent une <xref:System.InvalidOperationException> exception, et `Create` méthodes lèvent une <xref:System.Reflection.TargetInvocationException> exception avec une exception interne <xref:System.InvalidOperationException> exception.  
  
 Si votre application s’exécute sur les ordinateurs dont les configurations requièrent une conformité à la norme FIPS et que votre application utilise un algorithme qui n’est pas conforme à la norme FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) à partir de appliquer la conformité FIPS. Cet élément a été introduit dans .NET Framework 2.0 Service Pack 1.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Modèle de chiffrement](../../../../../docs/standard/security/cryptography-model.md)
