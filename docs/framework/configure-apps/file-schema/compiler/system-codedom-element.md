---
title: <system.codedom>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155386"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<compilateurs>](compilers-element.md)|Conteneur pour éléments de configuration de compilateur; contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes   
  
## <a name="net-framework-version-20"></a>.NET Version-cadre 2.0  
 [ \<L’élément system.codedom>](system-codedom-element.md) contient des paramètres de configuration compilateur pour les fournisseurs de langues installés sur un <xref:Microsoft.CSharp.CSharpCodeProvider> ordinateur <xref:Microsoft.VisualBasic.VBCodeProvider>en plus des fournisseurs par défaut qui sont installés avec le cadre .NET, tels que le et le . Les [ \<compilateurs>](compilers-element.md) élément contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments. Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.  
  
 Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres <xref:System.CodeDom.Compiler.CodeDomProvider> de configuration au fichier de configuration de la machine (Machine.config) pour une nouvelle implémentation. Utilisez <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> la méthode pour énumérer programmatiquement les fournisseurs de langues par défaut et les fournisseurs de langues identifiés par les paramètres de configuration du compilateur sur un ordinateur.  
  
> [!NOTE]
> Dans les versions cadre .NET 1.0 et 1.1, les fournisseurs de langue par défaut fournis par le cadre .NET sont identifiés dans les [ \<compilateurs>](compilers-element.md) élément. Dans la version cadre .NET 2.0, les fournisseurs de langage par défaut ne sont pas identifiés <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> dans les [ \<compilateurs>](compilers-element.md) élément, mais peuvent être énumérés à l’aide de la méthode.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Versions-cadre 1.0 et 1.1  
 [ \<L’élément system.codedom>](system-codedom-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langues sur un ordinateur. Les [ \<compilateurs>](compilers-element.md) élément contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments. Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de la machine et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant illustre une configuration compilateur typique.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Configuration Fichier Schema](../index.md)
- [Compilateur et Paramètres de fournisseur de langues Schema](index.md)
- [\<compilateur> Element](compiler-element.md)
