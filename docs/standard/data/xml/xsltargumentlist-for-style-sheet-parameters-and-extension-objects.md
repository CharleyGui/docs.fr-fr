---
title: XsltArgumentList pour les paramètres de feuille de style et les objets d'extension
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 6f0be433abcebed7f9da70225563a04170426314
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818204"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>XsltArgumentList pour les paramètres de feuille de style et les objets d'extension
La classe <xref:System.Xml.Xsl.XsltArgumentList> contient des paramètres XSLT (Extensible Stylesheet Language for Transformations) et des objets d'extension XSLT. Lorsqu’ils sont transmis à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, ces paramètres et ces objets d’extension peuvent être appelés à partir des feuilles de style.  
  
> [!NOTE]
> Les classes <xref:System.Xml.Xsl.XslTransform> et <xref:System.Xml.Xsl.XsltArgumentList> sont obsolètes dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).  
  
 La classe <xref:System.Xml.Xsl.XsltArgumentList> contient des paramètres XSLT et des objets d’extension XSLT. Lorsqu’ils sont transmis à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, ces paramètres et ces objets d’extension peuvent être appelés à partir des feuilles de style.  
  
 La transmission d'un objet plutôt que l'utilisation d'un script incorporé présente les avantages suivants :  
  
- Offre une meilleure encapsulation et réutilisation des classes.  
  
- Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.  
  
- Prend en charge des méthodes d'appel sur les classes appartenant à des espaces de noms autres que ceux définis dans l'ensemble des espaces de noms <xref:System> pris en charge.  
  
- Prend en charge la transmission de fragments d'arborescence résultat à la feuille de style à l'aide de l'objet <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Paramètres de feuille de style XSLT  
 Des paramètres XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. Un nom qualifié et un URI d'espace de noms sont associés à l'objet paramètre à ce stade.  
  
 L’objet paramètre doit correspondre à un type World Wide Web Consortium (W3C). Le tableau suivant présente les types W3C correspondants, les classes .NET Framework équivalentes (type) et indique si le type W3C est un type XML Path Language (XPath) ou un type XSLT.  
  
|Type W3C|Classe .NET Framework équivalente (type)|Type XPath ou type XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Booléen|System.Boolean|XPath|  
|Number|System.Double|XPath|  
|Fragment d’arborescence résultat|System.Xml.XPath.XPathNavigator|XSLT|  
|Collection de nœuds|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Si l'objet paramètre ne fait pas partie des classes ci-avant, il devient un type Double ou String, selon le cas. Les types Int16, UInt16, Int32, UInt32, Int64, UInt64, Single et Decimal deviennent un type Double. Tous les autres types deviennent un type String à l'aide de la méthode `ToString`.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Pour utiliser le paramètre XSLT, vous devez procéder comme suit :  
  
1. Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez les objets à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Appelez les paramètres à partir de la feuille de style.  
  
3. Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> pour créer un paramètre destiné à contenir une date de remise calculée. La date de la remise correspond à 20 jours à partir de la date de la commande.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
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
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a>Entrée  
 order.xml  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 discount.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Output  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a>Objets d'extension XSLT  
 Des objets d’extension XSLT sont ajoutés à l’objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.  
  
 Lors de l'ajout d'un objet, l'appelant de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> doit être d'un niveau de confiance suffisant dans la stratégie de sécurité. Si l'appelant est d'un niveau de confiance partiel, l'ajout n'aboutira pas.  
  
 L'ajout correct d'un objet ne garantit pas le succès de l'exécution. Lorsque la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est appelée, les autorisations sont calculées par rapport aux preuves fournies lors de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>, et ce jeu d'autorisations est attribué à l'ensemble du processus de transformation. Si un objet d’extension tente d’initier une action qui nécessite des autorisations qui ne se trouvent pas dans le jeu, une exception est levée.  
  
 Les types de données retournés par les objets d’extension correspondent à l’un des quatre types de données de base XPath : nombre, chaîne, booléen et collection de nœuds.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Pour utiliser l’objet d’extension XSLT, vous devez procéder comme suit :  
  
1. Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l’objet extension à l’aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Appelez l'objet d'extension à partir de la feuille de style.  
  
3. Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant calcule la circonférence d'un cercle en fonction de son rayon.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
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
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>Entrée  
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
  
 circle.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Output  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
