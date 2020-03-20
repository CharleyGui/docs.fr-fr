---
title: Élément <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155412"
---
# <a name="compilers-element"></a>\<compilateurs> Element
Conteneur pour éléments de configuration de compilateur; contient zéro ou plus [ \<compilateur>](compiler-element.md) éléments.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilateurs>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<compilateur> Element](compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration> Element](../configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
  
## <a name="remarks"></a>Notes   
 Les [ \<compilateurs>'élément](compilers-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langues sur un ordinateur. Chaque [ \<compilateur>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langue spécifique.  
  
 Le cadre .NET définit les paramètres initiaux du compilateur et du fournisseur de langues dans le fichier de configuration de la machine (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de la machine et le fichier de configuration d’application.  
  
## <a name="example"></a> Exemple  
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
- [Configuration Fichier Schema](../index.md)
- [Compilateur et Paramètres de fournisseur de langues Schema](index.md)
- [\<compilateur> Element](compiler-element.md)
