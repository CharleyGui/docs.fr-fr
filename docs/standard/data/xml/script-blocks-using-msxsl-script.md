---
title: Blocs de scripts utilisant msxsl:script
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: a63452df16e452a90eff3977ac8726cc0a5ac439
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710191"
---
# <a name="script-blocks-using-msxslscript"></a>Blocs de scripts utilisant msxsl:script
La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge les scripts incorporés en utilisant l'élément `msxsl:script`. Lorsque la feuille de style est chargée, toute fonction définie est compilée en langage MSIL (Microsoft Intermediate Language) par le CodeDOM (Code Document Object Model) et exécutée au cours de l’exécution. L' assembly généré à partir du bloc de script incorporé est distinct de l'assembly généré pour la feuille de style.  
  
## <a name="enable-xslt-script"></a>Activer les scripts XSLT  
 La prise en charge des scripts incorporés est un réglage XSLT facultatif de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. La prise en charge des scripts est désactivée par défaut. Pour l'activer, créez un objet <xref:System.Xml.Xsl.XsltSettings> avec la propriété <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> définie sur `true` et transmettez l'objet à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
> [!NOTE]
> Le script XSLT ne doit être activé que si la prise en charge des scripts est nécessaire et si vous travaillez dans un environnement totalement fiable.  
  
## <a name="msxslscript-element-definition"></a>Définition de l'élément msxsl:script  
 L’élément `msxsl:script` est une extension Microsoft de la recommandation XSLT 1.0. Il se définit comme suit :  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Le préfixe `msxsl` est lié à l'URI d'espace de noms `urn:schemas-microsoft-com:xslt`. La feuille de style doit inclure la déclaration d'espace de noms `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 L'attribut `language` est facultatif. Sa valeur est le langage du bloc de code incorporé. Ce langage est mappé au compilateur CodeDOM approprié à l’aide de la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType>. La classe <xref:System.Xml.Xsl.XslCompiledTransform> peut prendre en charge tout langage Microsoft .NET, à condition que le fournisseur approprié soit installé sur l'ordinateur et enregistré dans la section system.codedom du fichier machine.config. Si aucun attribut `language` n'est spécifié, le langage par défaut est JScript. Le nom du langage ne respecte pas la casse : les termes « JavaScript » et « javascript » sont équivalents.  
  
 L'attribut `implements-prefix` est obligatoire. Cet attribut est utilisé pour déclarer un espace de noms et l'associer au bloc de script. La valeur de cet attribut est le préfixe qui représente l'espace de noms. Ce préfixe peut être défini à un endroit d'une feuille de style.  
  
> [!NOTE]
> Lors de l'utilisation de l'élément `msxsl:script`, il est vivement recommandé de placer le script (quel que soit son langage) dans une section CDATA. Étant donné que le script peut contenir des opérateurs, identificateurs ou délimiteurs pour un langage donné, s'il n'est pas contenu dans une section CDATA, il risque d'être interprété à tort comme du XML. Le XML suivant illustre un modèle de la section CDATA où peut être placé le code.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Fonctions de script  
 Les fonctions peuvent être déclarées dans l'élément `msxsl:script`. Lorsqu'une fonction est déclarée, elle est contenue dans un bloc de script. Les feuilles de style peuvent contenir plusieurs blocs de scripts, chacun fonctionnant indépendamment des autres. Ainsi, si vous êtes en cours d'exécution dans un bloc de script, vous ne pouvez pas appeler une fonction que vous avez définie dans un autre bloc de script, sauf si elle est déclarée comme possédant le même espace de noms et le même langage de script. Puisque chaque bloc de script peut être écrit dans son propre langage et que le bloc est analysé en fonction des règles grammaticales de cet analyseur de langage, il est recommandé d'utiliser la syntaxe correcte pour le langage utilisé. Par exemple, si vous êtes dans un bloc de script Microsoft C#, utilisez la syntaxe de commentaires C#.  
  
 Les arguments fournis et les valeurs retournées par la fonction peuvent être de n’importe quel type. Les types XPath W3C étant un sous-ensemble des types CLR (common language runtime), une conversion de type est appliquée aux types qui ne sont pas considérés comme des types XPath. Le tableau suivant indique les correspondances entre les types W3C et les types CLR.  
  
|Type W3C|Type CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 Les types CLR numériques sont convertis en objet <xref:System.Double>. Le type <xref:System.DateTime> est converti en <xref:System.String>. Les types <xref:System.Xml.XPath.IXPathNavigable> sont convertis en <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator[]** est converti en objet <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Tous les autres types provoquent une erreur.  
  
### <a name="importing-namespaces-and-assemblies"></a>Importation d'espaces de noms et d'assemblys  
 La classe <xref:System.Xml.Xsl.XslCompiledTransform> prédéfinit un ensemble d'assemblys et d'espaces de noms qui sont pris en charge par défaut par l'élément `msxsl:script`. Cependant, vous pouvez utiliser des classes et des membres appartenant à un espace de noms qui ne figure pas sur la liste prédéfinie en important l'assembly et l'espace de noms dans un bloc `msxsl:script`.  
  
#### <a name="assemblies"></a>Assemblys  
 Les deux assemblys suivants sont référencés par défaut :  
  
- System.dll  
  
- System.Xml.dll  
  
- Microsoft.VisualBasic.dll (lorsque le langage de script est VB)  
  
 Vous pouvez importer les assemblys supplémentaires en utilisant l'élément `msxsl:assembly`. Cela comprend l'assembly lorsque la feuille de style est compilée. L'élément `msxsl:assembly` a la définition suivante :  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 L'attribut `name` contient le nom de l'assembly et l'attribut `href` contient le chemin de l'assembly. Le nom de l'assembly peut être un nom complet, comme « System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 », ou un nom court, comme « System.Web ».  
  
#### <a name="namespaces"></a>Espaces de noms  
 Les espaces de noms suivants sont inclus par défaut :  
  
- Système  
  
- System.Collection  
  
- System.Text  
  
- System.Text.RegularExpressions  
  
- System.Xml  
  
- System.Xml.Xsl  
  
- System.Xml.XPath  
  
- Microsoft.VisualBasic (lorsque le langage de script est VB)  
  
 Vous pouvez ajouter la prise en charge d'autres espaces de noms à l'aide de l'attribut `namespace`. La valeur de l'attribut est le nom de l'espace de noms.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise un script incorporé pour calculer la circonférence d'un cercle en fonction de son rayon.  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>number.xml  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>calc.xsl  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a>Output  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Génération et compilation de code source dynamique](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
