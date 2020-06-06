---
title: Élément <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115656"
---
# <a name="supportportability-element"></a>Élément \<supportPortability>
Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|PKT|Attribut requis.<br /><br /> Spécifie le jeton de clé publique de l’assembly affecté, sous la forme d’une chaîne.|  
|enabled|Attribut facultatif.<br /><br /> Spécifie si la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié doit être activée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Active la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié. Il s'agit de la valeur par défaut.|  
|false|Désactive la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié. Cela permet à l’application d’avoir des références à plusieurs implémentations de l’assembly spécifié.|  
  
### <a name="child-elements"></a>Éléments enfants  

Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
  
## <a name="remarks"></a>Remarques  

À partir de la .NET Framework 4, la prise en charge est automatiquement fournie pour les applications qui peuvent utiliser l’une des deux implémentations du .NET Framework, par exemple l’implémentation .NET Framework ou l’implémentation .NET Framework pour Silverlight. Les deux implémentations d’un assembly .NET Framework particulier sont considérées comme équivalentes par le Binder d’assembly. Dans certains scénarios, cette fonctionnalité de portabilité des applications provoque des problèmes. Dans ces scénarios, l' `<supportPortability>` élément peut être utilisé pour désactiver la fonctionnalité.  
  
Un tel scénario est un assembly qui doit référencer à la fois l’implémentation de .NET Framework et la .NET Framework pour l’implémentation Silverlight d’un assembly de référence particulier. Par exemple, un concepteur XAML écrit en Windows Presentation Foundation (WPF) devra peut-être référencer à la fois l’implémentation du Bureau WPF, l’interface utilisateur du concepteur et le sous-ensemble de WPF inclus dans l’implémentation Silverlight. Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents. Cet élément désactive le comportement par défaut et permet à la compilation de se dérouler correctement.  
  
> [!IMPORTANT]
> Pour que le compilateur passe les informations à la logique de liaison d’assembly du common language runtime, vous devez utiliser l' `/appconfig` option du compilateur pour spécifier l’emplacement du fichier app. config qui contient cet élément.  
  
## <a name="example"></a>Exemple  

L’exemple suivant permet à une application d’avoir des références à l’implémentation de .NET Framework et à la .NET Framework pour l’implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations. L' `/appconfig` option de compilateur doit être utilisée pour spécifier l’emplacement de ce fichier app. config.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [-appconfig (Options du compilateur C#)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Vue d’ensemble de l’unification des assemblys .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
