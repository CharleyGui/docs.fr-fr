---
title: Élément <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154203"
---
# <a name="dependentassembly-element"></a>\<dependentAssembly> Element
Encapsule la stratégie de liaisons et l’emplacement de chaque assembly. Utilisez `dependentAssembly` un élément pour chaque assemblage.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dépendantAssembly>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyIdentity`|Contient des informations d’identification sur l’assemblage. Cet élément doit être `dependentAssembly` inclus dans chaque élément.|  
|`codeBase`|Précise où l’heure d’exécution peut trouver un assemblage partagé s’il n’est pas installé sur l’ordinateur.|  
|`bindingRedirect`|Redirige une version d'assembly vers une autre.|  
|`publisherPolicy`|Précise si le temps d’exécution applique la politique de l’éditeur pour cette assemblée.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment encapsuler l’information d’assemblage pour deux assemblées.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
