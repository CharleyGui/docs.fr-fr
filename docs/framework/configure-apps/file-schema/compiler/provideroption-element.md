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
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155399"
---
# <a name="provideroption-element"></a>\<fournisseurOption> Element
Spécifie les attributs de la version compilateur pour un fournisseur de langue.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilateurs>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilateur>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<fournisseurOption>**

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
|`name`|Attribut requis.<br /><br /> Précise le nom de l’option; par exemple, "CompilerVersion".|  
|`value`|Attribut requis.<br /><br /> Spécifie la valeur de l’option; par exemple, "v3.5".|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration> Element](../configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
|[\<compilateurs> Element](compilers-element.md)|Conteneur pour éléments de configuration de compilateur; contient zéro `<compiler>` ou plus d’éléments.|  
|[\<compilateur> Element](compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
## <a name="remarks"></a>Notes   
 Dans la version cadre .NET 3.5, les fournisseurs de code Code Document Object `<providerOption>` Model (CodeDOM) peuvent prendre en charge les options spécifiques au fournisseur en utilisant l’élément.  
  
 Le cadre .NET 3.5 comprend des assemblages .NET Framework 2.0 mis à jour et fournit de nouvelles versions 3.5 assemblages qui contiennent de nouveaux types. Les fournisseurs de code Microsoft C et Visual Basic sont contenus dans les assemblages .NET Framework 2.0, mais ont été mis à jour pour prendre en charge les compilateurs de la version 3.5. Par défaut, les fournisseurs de code mis à jour génèrent du code pour les compilateurs de la version 2.0. Vous pouvez `<providerOption>` utiliser l’élément pour modifier la version compilateur cible à 3,5. Pour ce faire, spécifiez `name` "CompilerVersion" pour l’attribut et "v3.5" pour l’attribut. `value` Vous devez précéder le numéro de version avec un "v" minuscule.  
  
 Vous pouvez rendre la spécification de `<providerOption>` la version globale en ajoutant l’élément au fichier .NET Framework 2.0 Machine.config ou Root Web.config. Si vous mettez à jour la version compilateur par défaut à 3,5 dans le fichier Machine.config, vous `<providerOption>` pouvez la revenons à 2,0 sur une base par application en utilisant l’élément dans le fichier de configuration d’application.  
  
 CodeDOM codeD code provider implementers peut traiter les `providerOptions` options <xref:System.Collections.Generic.IDictionary%602>personnalisées en fournissant un constructeur qui prend un paramètre de type .  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment spécifier la version 3.5 du fournisseur de code CMD doit être utilisée.  
  
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
- [Configuration Fichier Schema](../index.md)
- [\<compilateurs> Element](compilers-element.md)
- [Spécification des noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compiler, élément de compilers pour compilation (Schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
