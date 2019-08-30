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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168916"
---
# <a name="systemcodedom-element"></a>\<System. CodeDom >, élément
Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. CodeDom >**  
  
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
|[\<compilers>](compilers-element.md)|Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="net-framework-version-20"></a>.NET Framework version 2,0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> L' [ \<élément System. CodeDom >](system-codedom-element.md) contient des paramètres de configuration du compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que et. <xref:Microsoft.VisualBasic.VBCodeProvider>. Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) . Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)  
  
 Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur ( <xref:System.CodeDom.Compiler.CodeDomProvider> machine. config) pour une nouvelle implémentation. Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.  
  
> [!NOTE]
> Dans les versions 1,0 et 1,1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework [ \<](compilers-element.md) sont identifiés dans l’élément >s de compilateurs. Dans la .NET Framework version 2,0, les fournisseurs de langages par défaut ne sont pas identifiés dans les [ \<compilateurs >](compilers-element.md) élément, mais peuvent être énumérés <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> à l’aide de la méthode.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework les versions 1,0 et 1,1  
 L’élément System [. CodeDom > contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. \<](system-codedom-element.md) Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) . Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)  
  
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
- [Schéma des fichiers de configuration](../index.md)
- [Schéma des paramètres du fournisseur de langage et du compilateur](index.md)
- [\<compiler> Element](compiler-element.md)
