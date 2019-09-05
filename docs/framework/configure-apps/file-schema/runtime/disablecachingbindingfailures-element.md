---
title: Élément <disableCachingBindingFailures>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5b45ea4b30677d17e72685b16c19f9192c8c144
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252680"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures >, élément
Spécifie s’il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut désactiver la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|`Value`|Description|  
|-----------|-----------------|  
|0|Ne désactivez pas la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection. Il s’agit du comportement de liaison par défaut à partir de la version 2,0 de .NET Framework.|  
|1|Désactivez la mise en cache des échecs de liaison qui se produisent parce que l’assembly est introuvable par la détection. Ce paramètre revient au comportement de liaison du .NET Framework version 1,1.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À partir de la version 2,0 de .NET Framework, le comportement par défaut pour le chargement des assemblys consiste à mettre en cache toutes les erreurs de liaison et de chargement. Autrement dit, si une tentative de chargement d’un assembly échoue, les demandes suivantes de chargement du même assembly échouent immédiatement, sans aucune tentative de localisation de l’assembly. Cet élément désactive le comportement par défaut pour les échecs de liaison qui se produisent parce que l’assembly est introuvable dans le chemin d’accès de détection. Ces échecs lèvent <xref:System.IO.FileNotFoundException>.  
  
 Certains échecs de liaison et de chargement ne sont pas affectés par cet élément et sont toujours mis en cache. Ces échecs se produisent parce que l’assembly a été trouvé mais n’a pas pu être chargé. Elles <xref:System.BadImageFormatException> lèvent <xref:System.IO.FileLoadException>ou. La liste suivante présente quelques exemples de tels échecs.  
  
- Si vous essayez de charger un fichier qui n’est pas un assembly valide, les tentatives suivantes de chargement de l’assembly échouent même si le fichier incorrect est remplacé par l’assembly approprié.  
  
- Si vous essayez de charger un assembly qui est verrouillé par le système de fichiers, les tentatives suivantes de chargement de l’assembly échouent même après la libération de l’assembly par le système de fichiers.  
  
- Si une ou plusieurs versions de l’assembly que vous tentez de charger se trouvent dans le chemin d’accès de détection, mais que la version spécifique que vous demandez n’est pas parmi celles-ci, les tentatives de chargement ultérieures de cette version échouent même si la version correcte est déplacée dans le chemin d’accès de détection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver la mise en cache des échecs de liaison d’assembly qui se produisent parce que l’assembly n’a pas été trouvé par la détection.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
