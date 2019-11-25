---
title: Élément <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088059"
---
# <a name="compiler-element"></a>Élément > du compilateur \<

Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. codedom**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**compilateurs**](compilers-element.md)\<
&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >

## <a name="syntax"></a>Syntaxe

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`compilerOptions`|Attribut facultatif.<br /><br /> Spécifie des arguments supplémentaires spécifiques au compilateur pour la compilation. Les valeurs de l’attribut `compilerOptions` sont généralement répertoriées dans une rubrique Options du compilateur pour le compilateur.|
|`extension`|Attribut requis.<br /><br /> Fournit une liste séparée par des points-virgules des extensions de nom de fichier utilisées par les fichiers sources pour le fournisseur de langages. Par exemple, « . cs ».|
|`language`|Attribut requis.<br /><br /> Fournit une liste séparée par des points-virgules des noms de langage pris en charge par le fournisseur de langages. Par exemple, « c#; CS ; CSharp ».|
|`type`|Attribut requis.<br /><br /> Spécifie le nom de type du fournisseur de langages, y compris le nom de l’assembly contenant l’implémentation du fournisseur. Le nom de type doit satisfaire aux spécifications définies dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|
|`warningLevel`|Attribut facultatif.<br /><br /> Spécifie le niveau d’avertissement du compilateur par défaut ; détermine le niveau auquel le fournisseur de langages traite les avertissements de compilation comme des erreurs.|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[\<élément providerOption >](provideroption-element.md)|Spécifie les attributs de version du compilateur pour un fournisseur de langage.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[\<configuration>, élément](../configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|[\<l’élément System. CodeDom >](system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|
|[\<les compilateurs > élément](compilers-element.md)|Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs éléments `<compiler>`.|

## <a name="remarks"></a>Notes

Chaque élément `<compiler>` spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique. Le fournisseur étend la classe <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> pour un langage spécifique. l’élément `<compiler>` définit les paramètres du compilateur et du générateur de code pour le fournisseur de langage.

Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.

Les éléments du compilateur dans le fichier de configuration Web ou d’application peuvent compléter ou substituer les paramètres dans le fichier de configuration de l’ordinateur. Si plusieurs implémentations de fournisseur sont configurées pour le même nom de langue ou la même extension de fichier, la dernière configuration correspondante remplace tous les fournisseurs configurés précédents pour ce nom de langue ou cette extension de fichier.

## <a name="configuration-file"></a>Fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.

## <a name="example"></a>Exemple

L’exemple suivant illustre un élément de configuration de compilateur classique :

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
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma des fichiers de configuration](../index.md)
- [\<les compilateurs > élément](compilers-element.md)
- [Spécification des noms de types complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compiler, élément de compilateurs pour compilation (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
