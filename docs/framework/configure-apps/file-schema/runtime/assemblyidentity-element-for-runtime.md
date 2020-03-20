---
title: Élément <assemblyIdentity> pour <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154307"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblageIdentity> Element pour \<les> de temps d’exécution
Contient des informations d’identification sur l’assemblage.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dépendantAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblageIdentity>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Le nom de l’assemblée|  
|`culture`|Attribut facultatif.<br /><br /> Une chaîne qui spécifie la langue et le pays/région de l’assemblée.|  
|`publicKeyToken`|Attribut facultatif.<br /><br /> Une valeur hexadecimale qui spécifie le nom fort de l’assemblage.|  
|`processorArchitecture`|Attribut facultatif.<br /><br /> L’une des valeurs "x86", "amd64", "msil", ou "ia64", précisant l’architecture du processeur pour un assemblage contenant du code spécifique au processeur. Les valeurs ne sont pas sensibles aux cas. Si l’attribut est attribué à `<assemblyIdentity>` toute autre valeur, l’élément entier est ignoré. Consultez <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processeurArchitecture Attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|`amd64`|ARCHITECTURE AMD x86-64 seulement.|  
|`ia64`|Intel Itanium architecture seulement.|  
|`msil`|Neutre en ce qui concerne le processeur et les bits par mot.|  
|`x86`|Un processeur x86 32 bits, natif ou dans l’environnement Windows on Windows (WOW) sur une plate-forme 64 bits.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`dependentAssembly`|Encapsule la stratégie de liaisons et l’emplacement de chaque assembly. Utilisez `<dependentAssembly>` un élément pour chaque assemblage.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Chaque ** \<élément>dépendant** doit avoir une ** \<assembléeIdentity>** élément enfant.  
  
 Si `processorArchitecture` l’attribut est `<assemblyIdentity>` présent, l’élément ne s’applique qu’à l’assemblage avec l’architecture correspondante du processeur. Si `processorArchitecture` l’attribut n’est pas présent, l’élément `<assemblyIdentity>` peut s’appliquer à un assemblage avec n’importe quelle architecture de processeur.  
  
 L’exemple suivant montre un fichier de configuration pour deux assemblages du même nom qui ciblent deux architectures de processeur différentes, et dont les versions n’ont pas été maintenues en synchronisation. Lorsque l’application s’exécute sur la `<assemblyIdentity>` plate-forme x86, le premier élément s’applique et l’autre est ignoré. Si l’application s’exécute sur une plate-forme autre que x86 ou ia64, les deux sont ignorés.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Si un fichier `<assemblyIdentity>` de configuration `processorArchitecture` contient un élément sans attribut et ne contient `processorArchitecture` pas d’élément qui correspond à la plate-forme, l’élément sans l’attribut est utilisé.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment fournir des informations sur une assemblée.  
  
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
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
