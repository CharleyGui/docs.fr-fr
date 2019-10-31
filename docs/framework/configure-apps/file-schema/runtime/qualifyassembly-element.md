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
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115781"
---
# <a name="qualifyassembly-element"></a>\<élément qualifyAssembly >
Spécifie le nom complet de l'assembly qui doit être chargé dynamiquement quand un nom partiel est utilisé.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**qualifyAssembly >**  
  
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
|`partialName`|Attribut requis.<br /><br /> Spécifie le nom partiel de l’assembly tel qu’il apparaît dans le code.|  
|`fullName`|Attribut requis.<br /><br /> Spécifie le nom complet de l’assembly tel qu’il apparaît dans la Global Assembly Cache.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 L’appel de la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> à l’aide de noms d’assemblys partiels fait que le common language runtime recherche l’assembly uniquement dans le répertoire de base de l’application. Utilisez l’élément **\<qualifyAssembly >** dans le fichier de configuration de votre application pour fournir les informations complètes sur l’assembly (nom, version, jeton de clé publique et culture) et faire en sorte que l’Common Language Runtime recherche l’assembly dans le Global cache d’assembly.  
  
 L’attribut **FullName** doit inclure les quatre champs d’identité d’assembly : nom, version, jeton de clé publique et culture. L’attribut **partialName** doit référencer partiellement un assembly. Vous devez spécifier au moins le nom du texte de l’assembly (le cas le plus courant), mais vous pouvez également inclure la version, le jeton de clé publique ou la culture (ou n’importe quelle combinaison des quatre, mais pas les quatre). L' **partialName** doit correspondre au nom spécifié dans votre appel. Par exemple, vous ne pouvez pas spécifier `"math"` comme attribut **partialName** dans votre fichier de configuration et appeler `Assembly.Load("math, Version=3.3.3.3")` dans votre code.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit logiquement l’appel `Assembly.Load("math")` en `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
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

- [Schéma des paramètres d’exécution](index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Références d’assembly partielles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
