---
title: Élément <assemblyBinding> pour <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: b6a39bcecfd2485481677496adcf026d986c283b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170244"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblyBinding>, élément de \<runtime>

Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**xmlns**|Attribut requis.<br /><br /> Spécifie l'espace de noms XML requis pour la liaison d'assembly. Utilisez la chaîne « urn:schemas-microsoft-com:asm.v1 » comme valeur.|  
|**appliesTo**|Spécifie la version du runtime à laquelle s'applique la redirection d'assembly .NET Framework. Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique. Si aucun attribut **appliesTo** n’est spécifié, l' **\<assemblyBinding>** élément s’applique à toutes les versions du .NET Framework. L’attribut **appliesTo** a été introduit dans .NET Framework version 1,1 ; elle est ignorée par la version de .NET Framework 1,0. Cela signifie que tous les **\<assemblyBinding>** éléments sont appliqués lors de l’utilisation de la version 1,0 de .NET Framework, même si un attribut **appliesTo** est spécifié.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|Encapsule la stratégie de liaison et l'emplacement d'un assembly. Utilisez une **\<dependentAssembly>** balise pour chaque assembly.|  
|[\<probing>](probing-element.md)|Spécifie les sous-répertoires interrogés par le Common Language Runtime lors du chargement des assemblys.|  
|[\<publisherPolicy>](publisherpolicy-element.md)|Spécifie si le runtime applique la stratégie de l'éditeur.|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment rediriger une version d'assembly vers une autre et fournir une base de code.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L’exemple suivant montre comment utiliser l’attribut **appliesTo** pour rediriger la liaison d’un assembly de .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
- [Redirection des versions d'assemblys](../../redirect-assembly-versions.md)
