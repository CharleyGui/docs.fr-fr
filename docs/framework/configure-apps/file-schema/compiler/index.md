---
title: Schéma des paramètres du fournisseur de langage et du compilateur
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 4900c391ae94447cdf4be331a27f6f3398e9129a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659719"
---
# <a name="compiler-and-language-provider-settings-schema"></a>Schéma des paramètres du fournisseur de langage et du compilateur
Les paramètres du compilateur et du fournisseur de langage spécifient les éléments de configuration du compilateur pour les fournisseurs de langages disponibles. Chaque élément de configuration du compilateur spécifie le nom du type de fournisseur de code, les paramètres du compilateur, les noms des langages pris en charge et les extensions de fichier prises en charge.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
 [\<configuration>, élément](../configuration-element.md)  
  
 [\<system.codedom>](system-codedom-element.md)  
  
 [\<compilers>](compilers-element.md)  
  
 [\<compiler>](compiler-element.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
|[\<compilers>](compilers-element.md)|Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).|  
|[\<compiler>](compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
## <a name="example"></a>Exemples  
 L’exemple suivant illustre un élément de configuration du compilateur classique.  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
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
- [\<compiler> Element](compiler-element.md)
