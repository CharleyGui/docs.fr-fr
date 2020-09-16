---
title: Élément <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 7e006adb86886d22ec08dc61fa092bf677b4da96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544737"
---
# <a name="provideroption-element"></a>Élément \<providerOption>
Spécifie les attributs de version du compilateur pour un fournisseur de langages.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut requis.<br /><br /> Spécifie le nom de l’option ; par exemple, « CompilerVersion ».|  
|`value`|Attribut requis.<br /><br /> Spécifie la valeur de l’option. par exemple, « v 3.5 ».|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration> Appartient](../configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom> Appartient](system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
|[\<compilers> Appartient](compilers-element.md)|Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs `<compiler>` éléments.|  
|[\<compiler> Appartient](compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
## <a name="remarks"></a>Notes  
 Dans la version 3,5, .NET Framework les fournisseurs de code Code Document Object Model (CodeDOM) peuvent prendre en charge des options spécifiques au fournisseur à l’aide de l' `<providerOption>` élément.  
  
 Le .NET Framework 3,5 inclut des assemblys .NET Framework 2,0 mis à jour et fournit de nouveaux assemblys de version 3,5 qui contiennent de nouveaux types. Les fournisseurs de code Microsoft C# et Visual Basic sont contenus dans les assemblys .NET Framework 2,0, mais ils ont été mis à jour pour prendre en charge les compilateurs de version 3,5. Par défaut, les fournisseurs de code mis à jour génèrent du code pour la version 2,0 des compilateurs. Vous pouvez utiliser l' `<providerOption>` élément pour remplacer la version du compilateur cible par 3,5. Pour ce faire, spécifiez « CompilerVersion » pour l' `name` attribut et « v 3.5 » pour l' `value` attribut. Vous devez faire précéder le numéro de version d’un « v » en minuscules.  
  
 Vous pouvez rendre la spécification de version globale en ajoutant l' `<providerOption>` élément au fichier .NET Framework 2,0 Machine.config ou racine Web.config. Si vous mettez à jour la version du compilateur par défaut vers 3,5 dans le fichier Machine.config, vous pouvez la remodifier en 2,0 pour chaque application à l’aide `<providerOption>` de l’élément dans le fichier de configuration de l’application.  
  
 Les implémenteurs de fournisseurs de code CodeDOM peuvent traiter des options personnalisées en fournissant un constructeur qui accepte un `providerOptions` paramètre de type <xref:System.Collections.Generic.IDictionary%602> .  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment spécifier que la version 3,5 du fournisseur de code C# doit être utilisée.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma du fichier de configuration](../index.md)
- [\<compilers> Appartient](compilers-element.md)
- [Spécification des noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compiler, élément de compilers pour compilation (Schéma des paramètres ASP.NET)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
