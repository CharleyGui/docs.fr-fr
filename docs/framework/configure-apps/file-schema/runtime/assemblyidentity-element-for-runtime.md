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
ms.openlocfilehash: f3e74b05ac0fd7c57963f2aad047ba3f2d63a10a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170179"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity>, élément de \<runtime>

Contient des informations d’identification sur l’assembly.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
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
|`name`|Attribut requis.<br /><br /> Nom de l’assembly|  
|`culture`|Attribut facultatif.<br /><br /> Chaîne qui spécifie la langue et le pays/la région de l’assembly.|  
|`publicKeyToken`|Attribut facultatif.<br /><br /> Valeur hexadécimale qui spécifie le nom fort de l’assembly.|  
|`processorArchitecture`|Attribut facultatif.<br /><br /> L’une des valeurs « x86 », « amd64 », « MSIL » ou « ia64 », spécifiant l’architecture de processeur pour un assembly qui contient du code spécifique au processeur. Les valeurs ne respectent pas la casse. Si une autre valeur est assignée à l’attribut, la totalité de l' `<assemblyIdentity>` élément est ignorée. Consultez <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|`amd64`|Architecture AMD x86-64 uniquement.|  
|`ia64`|Architecture Intel Itanium uniquement.|  
|`msil`|Neutre en ce qui concerne le processeur et les bits par mot.|  
|`x86`|Processeur x86 32 bits, natif ou dans l’environnement Windows sur Windows (WOW) sur une plateforme 64 bits.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`dependentAssembly`|Encapsule la stratégie de liaisons et l’emplacement de chaque assembly. Utilisez un seul `<dependentAssembly>` élément pour chaque assembly.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  

 Chaque **\<dependentAssembly>** élément doit avoir un **\<assemblyIdentity>** élément enfant.  
  
 Si l' `processorArchitecture` attribut est présent, l' `<assemblyIdentity>` élément s’applique uniquement à l’assembly avec l’architecture de processeur correspondante. Si l' `processorArchitecture` attribut n’est pas présent, l' `<assemblyIdentity>` élément peut s’appliquer à un assembly avec toute architecture de processeur.  
  
 L’exemple suivant montre un fichier de configuration pour deux assemblys portant le même nom et ciblant deux architectures à deux processeurs différentes, et dont les versions n’ont pas été conservées dans la synchronisation. Lorsque l’application s’exécute sur la plateforme x86, le premier `<assemblyIdentity>` élément s’applique et l’autre est ignorée. Si l’application s’exécute sur une plateforme autre que x86 ou ia64, les deux sont ignorées.  
  
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
  
 Si un fichier de configuration contient un `<assemblyIdentity>` élément sans `processorArchitecture` attribut et qu’il ne contient pas d’élément qui correspond à la plateforme, l’élément sans l' `processorArchitecture` attribut est utilisé.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment fournir des informations sur un assembly.  
  
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
- [Schéma du fichier de configuration](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
