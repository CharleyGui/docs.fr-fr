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
ms.openlocfilehash: 6c35e24696be040788a0c44cbb100ebb35d37157
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149567"
---
# <a name="systemcodedom-element"></a>Élément \<system.codedom>

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
|[\<compilers>](compilers-element.md)|Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="net-framework-version-20"></a>.NET Framework version 2,0  

 L' [\<system.codedom>](system-codedom-element.md) élément contient des paramètres de configuration du compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que <xref:Microsoft.CSharp.CSharpCodeProvider> et <xref:Microsoft.VisualBasic.VBCodeProvider> . L' [\<compilers>](compilers-element.md) élément contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments. Chaque [\<compiler>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.  
  
 Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur (Machine.config) pour une nouvelle <xref:System.CodeDom.Compiler.CodeDomProvider> implémentation. Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.  
  
> [!NOTE]
> Dans les versions 1,0 et 1,1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework sont identifiés dans l' [\<compilers>](compilers-element.md) élément. Dans la .NET Framework version 2,0, les fournisseurs de langage par défaut ne sont pas identifiés dans l' [\<compilers>](compilers-element.md) élément, mais peuvent être énumérés à l’aide de la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> méthode.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework les versions 1,0 et 1,1  

 L' [\<system.codedom>](system-codedom-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. L' [\<compilers>](compilers-element.md) élément contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments. Chaque [\<compiler>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
## <a name="configuration-file"></a>Fichier de configuration  

 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant illustre une configuration de compilateur classique.  
  
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
- [Schéma du fichier de configuration](../index.md)
- [Schéma des paramètres du fournisseur de langage et du compilateur](index.md)
- [\<compiler> Appartient](compiler-element.md)
