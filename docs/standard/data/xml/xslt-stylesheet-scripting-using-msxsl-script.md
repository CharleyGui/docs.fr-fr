---
title: Écriture de feuilles de style XSLT avec msxsl:script>
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 9bf57e0f74a353fb6512a24214e9479c1d813aab
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160207"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>Écriture de feuilles de style XSLT avec \<msxsl:script>
La classe <xref:System.Xml.Xsl.XslTransform> prend en charge les scripts incorporés en utilisant l'élément `script`.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 La classe <xref:System.Xml.Xsl.XslTransform> prend en charge les scripts incorporés en utilisant l'élément `script`. Lorsque la feuille de style est chargée, toute fonction définie est compilée en langage MSIL (Microsoft Intermediate Language) par son enveloppement dans une définition de classe et n'engendre aucune perte des performances.  
  
 L'élément `<msxsl:script>` est défini ci-après :  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 où `msxsl` est un préfixe lié à l'espace de noms `urn:schemas-microsoft-com:xslt`.  
  
 L’attribut `language` n’est pas obligatoire, mais s’il est spécifié, sa valeur doit être l’une des suivantes : `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`ou `CSharp`. Lorsqu'il n'est pas spécifié, le langage par défaut est JScript. Le `language-name` ne respecte pas la casse : les termes « JavaScript » et « javascript » sont équivalents.  
  
 L'attribut `implements-prefix` est obligatoire. Cet attribut est utilisé pour déclarer un espace de noms et l'associer au bloc de script. La valeur de cet attribut est le préfixe qui représente l'espace de noms. Cet espace de noms peut être défini à un endroit d'une feuille de style.  
  
 Dans la mesure où l'élément `msxsl:script` appartient à l'espace de noms `urn:schemas-microsoft-com:xslt`, la feuille de style doit inclure la déclaration d'espaces de noms `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Si l'appelant du script ne possède pas l'autorisation d'accès <xref:System.Security.Permissions.SecurityPermissionFlag>, le script présent dans une feuille de style ne se compilera jamais et l'appel à <xref:System.Xml.Xsl.XslTransform.Load%2A> échouera.  
  
 Si l'appelant possède une autorisation `UnmanagedCode`, le script se compile, mais les opérations autorisées sont dépendantes des preuves fournies au moment du chargement.  
  
 Si vous utilisez l'une des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prennent un objet <xref:System.Xml.XmlReader> ou un objet <xref:System.Xml.XPath.XPathNavigator> pour charger la feuille de style, vous devez utiliser la surcharge <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prend un paramètre <xref:System.Security.Policy.Evidence>. Pour fournir des preuves, l'appelant doit avoir l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag> pour fournir `Evidence` à l'assembly du script. Si l'appelant n'a pas cette autorisation, il peut attribuer la valeur `Evidence` au paramètre `null`. Cela entraîne l'échec de la fonction <xref:System.Xml.Xsl.XslTransform.Load%2A> si le script n'est pas trouvé. L'autorisation `ControlEvidence` est considérée comme une autorisation très puissante qui ne doit être accordée qu'au code d'un niveau de confiance élevé.  
  
 Pour obtenir la preuve de votre assembly, utilisez `this.GetType().Assembly.Evidence`. Pour obtenir la preuve d'un URI (Uniform Resource Identifier), utilisez `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Si vous utilisez les méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prennent un objet <xref:System.Xml.XmlResolver> mais aucun `Evidence`, la zone de sécurité pour l'assembly prend la valeur Confiance totale par défaut. Pour plus d'informations, consultez les pages <xref:System.Security.SecurityZone> et [Ensemble d'autorisations nommés](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Les fonctions peuvent être déclarées dans l'élément `msxsl:script`. Le tableau suivant montre les espaces de noms qui sont pris en charge par défaut. Vous pouvez utiliser des classes en dehors des espaces de noms répertoriés. Toutefois, ces classes doivent être qualifiées complètes.  
  
|Espaces de noms par défaut|Description|  
|------------------------|-----------------|  
|System|Classe système.|  
|System.Collection|Classes de collection.|  
|System.Text|Classes de texte.|  
|System.Text.RegularExpressions|Classes d'expressions régulières.|  
|System.Xml|Classes XML principales.|  
|System.Xml.Xsl|Classes XSLT.|  
|System.Xml.XPath|Classes XML Path Language (XPath).|  
|Microsoft.VisualBasic|Classes pour les scripts Microsoft Visual Basic.|  
  
 Lorsqu'une fonction est déclarée, elle est contenue dans un bloc de script. Les feuilles de style peuvent contenir plusieurs blocs de scripts, chacun fonctionnant indépendamment des autres. Ainsi, si vous êtes en cours d'exécution dans un bloc de script, vous ne pouvez pas appeler une fonction que vous avez définie dans un autre bloc de script, sauf si elle est déclarée comme possédant le même espace de noms et le même langage de script. Puisque chaque bloc de script peut être écrit dans son propre langage et que le bloc est analysé en fonction des règles grammaticales de cet analyseur de langage, vous devez utiliser la syntaxe correcte pour la langue utilisée. Par exemple, il n'est pas correct d'utiliser un nœud de commentaire XML `<!-- an XML comment -->` dans un bloc de script C#.  
  
 Les arguments fournis et les valeurs de retour définies par les fonctions du script doivent être l'un des types définis par le World Wide Web Consortium (W3C), XPath ou XSLT. Le tableau suivant illustre les types W3C correspondants, les classes .NET Framework équivalentes (Type), et précise si le type W3C est un XPath ou XSLT.  
  
|Type|Classe .NET Framework équivalente (Type)|Type XPath ou type XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Number|System.Double|XPath|  
|Fragment d’arborescence résultat|System.Xml.XPath.XPathNavigator|XSLT|  
|Collection de nœuds|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Si la fonction de script utilise l’un des types numériques suivants : Int16, UInt16, Int32, UInt32, Int64, UInt64, Single ou Decimal, ils deviennent Double, ce qui effectue un mappage sur le nombre de type XPath W3C. Tous les autres types deviennent une chaîne à l'aide de la méthode `ToString`.  
  
 Si la fonction de script utilise un type différent de ceux mentionnés ci-avant ou si la fonction ne se compile pas lorsque la feuille de style est chargée dans l'objet <xref:System.Xml.Xsl.XslTransform>, une exception est levée.  
  
 Si l'élément `msxsl:script` est utilisé, il est vivement recommandé de placer le script (quel que soit son langage) dans une section CDATA. Par exemple, le langage XML suivant illustre le modèle de la section CDATA dans laquelle est placé votre code.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Il est vivement recommandé de placer tout le contenu du script dans une section CDATA car les opérateurs, les identificateurs ou les délimiteurs d'un langage donné peuvent être mal interprétés en tant que XML. L'exemple suivant illustre l'utilisation de l'opérateur AND logique dans le script.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Cela lève une exception car les signes &amp; ne font pas l'objet d'un échappement. Le document est chargé en tant que XML et aucun traitement spécial n’est appliqué au texte qui se trouve entre les étiquettes d’élément `msxsl:script`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise un script incorporé pour calculer la circonférence d'un cercle en fonction de son rayon.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a>Entrée  
 number.xml  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 calc.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Sortie  
  
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

- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
