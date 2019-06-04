---
title: Élément <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab9feaa1c46a45471395fd4c6158490a24882a65
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489364"
---
# <a name="supportportability-element"></a>\<supportPortability > élément
Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.  
  
 \<configuration > élément  
\<runtime > élément  
\<assemblyBinding > élément  
\<supportPortability > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|PKT|Attribut requis.<br /><br /> Spécifie le jeton de clé publique de l’assembly affecté, sous forme de chaîne.|  
|enabled|Attribut facultatif.<br /><br /> Spécifie si la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié doit être activée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|true|Activer la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié. Il s'agit de la valeur par défaut.|  
|False|Désactiver la prise en charge pour la portabilité entre les implémentations de l’assembly .NET Framework spécifié. Cela permet à l’application d’avoir des références à plusieurs implémentations de l’assembly spécifié.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
|`assemblyBinding`|Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.|  
  
## <a name="remarks"></a>Notes  
 À compter de .NET Framework 4, prise en charge est automatiquement fournie pour les applications qui peuvent utiliser une des deux implémentations du .NET Framework, par exemple l’implémentation de .NET Framework ou .NET Framework pour l’implémentation Silverlight. Les deux implémentations d’un assembly .NET Framework particulier sont considérées comme équivalents par le binder d’assembly. Dans certains scénarios, cette fonctionnalité de portabilité d’application pose des problèmes. Dans ces scénarios, le `<supportPortability>` élément peut être utilisé pour désactiver la fonctionnalité.  
  
 Un tel scénario est un assembly qui doit faire référence à l’implémentation de .NET Framework et le .NET Framework pour l’implémentation Silverlight d’un assembly de référence particulier. Par exemple, un concepteur XAML écrit dans Windows Presentation Foundation (WPF) devrez peut-être faire référence à la fois l’implémentation de bureau WPF pour l’interface utilisateur du concepteur et le sous-ensemble de WPF, qui est inclus dans l’implémentation Silverlight. Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents. Cet élément désactive le comportement par défaut et permet la compilation de réussir.  
  
> [!IMPORTANT]
>  Pour que le compilateur passer les informations à la logique de liaison d’assembly du common language runtime, vous devez utiliser le `/appconfig` option du compilateur pour spécifier l’emplacement du fichier app.config qui contient cet élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant permet à une application d’avoir des références à l’implémentation de .NET Framework et le .NET Framework pour l’implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations. Le `/appconfig` option du compilateur doit être utilisée pour spécifier l’emplacement de ce fichier app.config.  
  
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

- [/appconfig (Options du compilateur C#)](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Vue d’ensemble du Unification des assemblys .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
