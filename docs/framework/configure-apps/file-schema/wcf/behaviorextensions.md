---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448683"
---
# \<behaviorExtensions>
Les extensions de comportement permettent la création d'éléments de comportement définis par l'utilisateur. Ces éléments peuvent être utilisés avec les éléments de comportement standard Windows Communication Foundation (WCF). La section `behaviorExtensions` définit l'élément tel qu'il peut être utilisé dans la configuration. Voici un exemple d'une extension de comportement typique.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Pour ajouter des capacités de configuration à l'élément, vous devez écrire et enregistrer un élément de configuration. Pour plus d'informations, consultez la documentation <xref:System.Configuration>.  
  
 Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée comme dans l’exemple suivant.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Sécurité  
 Il est fortement recommandé d'utiliser des noms d'assembly qualifiés complets lors de l'enregistrement de types dans les fichiers `machine.config` et `app.config`. Si le type n'est pas défini uniquement, le chargeur de type CLR le recherche dans les emplacements suivants dans l'ordre spécifié :  
  
 Si l'assembly du type est connu, le chargeur recherche les emplacements de redirection du fichier de configuration, GAC, l'assembly actuel à l'aide d'informations de configuration, et du répertoire de base de l'application. Si l'assembly est inconnu, le chargeur recherche l'assembly actuel, mscorlib, et l'emplacement retourné par le gestionnaire d'événements `TypeResolve`. Cet ordre de recherche du CLR peut être modifié avec les raccordements tels que le mécanisme de transfert de type et l'événement AppDomain.TypeResolve.  
  
 Un intrus peut exploiter l'ordre de recherche du CLR et exécuter le code non autorisé. L’utilisation de noms complets (forts) identifie de manière unique un type et renforce considérablement la sécurité de votre système.  
  
 Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../../../deployment/how-the-runtime-locates-assemblies.md) et <xref:System.AppDomain.TypeResolve> .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Configuration et extension de l'exécution à l'aide de comportements](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
