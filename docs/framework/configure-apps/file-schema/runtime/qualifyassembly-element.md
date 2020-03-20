---
title: Élément <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153917"
---
# <a name="qualifyassembly-element"></a>\<qualifierAssembly> Element
Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifierAssembly>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`partialName`|Attribut requis.<br /><br /> Spécifie le nom partiel de l’assemblage tel qu’il apparaît dans le code.|  
|`fullName`|Attribut requis.<br /><br /> Spécifie le nom complet de l’assemblée tel qu’il apparaît dans le cache d’assemblage global.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes   
 Appeler <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> la méthode en utilisant des noms d’assemblage partiel provoque le temps de course de langue commune de rechercher l’assemblage seulement dans l’annuaire de base d’application. Utilisez ** \<l’élément qualifieAssembly>** dans votre fichier de configuration d’application pour fournir les informations d’assemblage complète (nom, version, jeton de clé publique et culture) et provoquer l’heure d’exécution de la langue commune à rechercher l’assemblage dans le cache d’assemblage global.  
  
 **L’attribut FullName** doit inclure les quatre domaines de l’identité de l’assemblage : nom, version, jeton de clé publique et culture. **L’attribut partielnamise** doit en partie faire référence à une assemblée. Vous devez spécifier au moins le nom de texte de l’assemblée (le cas le plus courant), mais vous pouvez également inclure la version, le jeton de clé publique, ou la culture (ou toute combinaison des quatre, mais pas les quatre). Le **nom partiel** doit correspondre au nom spécifié dans votre appel. Par exemple, vous `"math"` ne pouvez pas spécifier `Assembly.Load("math, Version=3.3.3.3")` comme attribut **partielName** dans votre fichier de configuration et appeler dans votre code.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant transforme `Assembly.Load("math")` logiquement l’appel en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d'exécution](index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Références d'assembly partielles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
