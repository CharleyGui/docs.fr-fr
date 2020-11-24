---
title: XsltArgumentList pour les paramètres de feuille de style et les objets d'extension
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: fe227a2d3efc5c36b818b7f4431896e6f62b1f26
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685043"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="7d65c-102">XsltArgumentList pour les paramètres de feuille de style et les objets d'extension</span><span class="sxs-lookup"><span data-stu-id="7d65c-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>

<span data-ttu-id="7d65c-103">La classe <xref:System.Xml.Xsl.XsltArgumentList> contient des paramètres XSLT (Extensible Stylesheet Language for Transformations) et des objets d'extension XSLT.</span><span class="sxs-lookup"><span data-stu-id="7d65c-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="7d65c-104">Lorsqu’ils sont transmis à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, ces paramètres et ces objets d’extension peuvent être appelés à partir des feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="7d65c-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d65c-105">Les classes <xref:System.Xml.Xsl.XslTransform> et <xref:System.Xml.Xsl.XsltArgumentList> sont obsolètes dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="7d65c-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="7d65c-106">Vous pouvez effectuer des transformations XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="7d65c-107">Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="7d65c-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="7d65c-108">La classe <xref:System.Xml.Xsl.XsltArgumentList> contient des paramètres XSLT et des objets d’extension XSLT.</span><span class="sxs-lookup"><span data-stu-id="7d65c-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="7d65c-109">Lorsqu’ils sont transmis à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, ces paramètres et ces objets d’extension peuvent être appelés à partir des feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="7d65c-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="7d65c-110">La transmission d'un objet plutôt que l'utilisation d'un script incorporé présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d65c-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="7d65c-111">Offre une meilleure encapsulation et réutilisation des classes.</span><span class="sxs-lookup"><span data-stu-id="7d65c-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="7d65c-112">Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="7d65c-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="7d65c-113">Prend en charge des méthodes d'appel sur les classes appartenant à des espaces de noms autres que ceux définis dans l'ensemble des espaces de noms <xref:System> pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7d65c-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="7d65c-114">Prend en charge la transmission de fragments d'arborescence résultat à la feuille de style à l'aide de l'objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="7d65c-115">Paramètres de feuille de style XSLT</span><span class="sxs-lookup"><span data-stu-id="7d65c-115">XSLT Style Sheet Parameters</span></span>  

 <span data-ttu-id="7d65c-116">Des paramètres XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="7d65c-117">Un nom qualifié et un URI d'espace de noms sont associés à l'objet paramètre à ce stade.</span><span class="sxs-lookup"><span data-stu-id="7d65c-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="7d65c-118">L’objet paramètre doit correspondre à un type World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="7d65c-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="7d65c-119">Le tableau suivant présente les types W3C correspondants, les classes .NET Framework équivalentes (type) et indique si le type W3C est un type XML Path Language (XPath) ou un type XSLT.</span><span class="sxs-lookup"><span data-stu-id="7d65c-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="7d65c-120">Type W3C</span><span class="sxs-lookup"><span data-stu-id="7d65c-120">W3C Type</span></span>|<span data-ttu-id="7d65c-121">Classe .NET Framework équivalente (type)</span><span class="sxs-lookup"><span data-stu-id="7d65c-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="7d65c-122">Type XPath ou type XSLT</span><span class="sxs-lookup"><span data-stu-id="7d65c-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="7d65c-123">String</span><span class="sxs-lookup"><span data-stu-id="7d65c-123">String</span></span>|<span data-ttu-id="7d65c-124">System.String</span><span class="sxs-lookup"><span data-stu-id="7d65c-124">System.String</span></span>|<span data-ttu-id="7d65c-125">XPath</span><span class="sxs-lookup"><span data-stu-id="7d65c-125">XPath</span></span>|  
|<span data-ttu-id="7d65c-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="7d65c-126">Boolean</span></span>|<span data-ttu-id="7d65c-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="7d65c-127">System.Boolean</span></span>|<span data-ttu-id="7d65c-128">XPath</span><span class="sxs-lookup"><span data-stu-id="7d65c-128">XPath</span></span>|  
|<span data-ttu-id="7d65c-129">Number</span><span class="sxs-lookup"><span data-stu-id="7d65c-129">Number</span></span>|<span data-ttu-id="7d65c-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="7d65c-130">System.Double</span></span>|<span data-ttu-id="7d65c-131">XPath</span><span class="sxs-lookup"><span data-stu-id="7d65c-131">XPath</span></span>|  
|<span data-ttu-id="7d65c-132">Fragment d’arborescence résultat</span><span class="sxs-lookup"><span data-stu-id="7d65c-132">Result Tree Fragment</span></span>|<span data-ttu-id="7d65c-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="7d65c-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="7d65c-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="7d65c-134">XSLT</span></span>|  
|<span data-ttu-id="7d65c-135">Collection de nœuds</span><span class="sxs-lookup"><span data-stu-id="7d65c-135">Node Set</span></span>|<span data-ttu-id="7d65c-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="7d65c-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="7d65c-137">XPath</span><span class="sxs-lookup"><span data-stu-id="7d65c-137">XPath</span></span>|  
  
 <span data-ttu-id="7d65c-138">Si l'objet paramètre ne fait pas partie des classes ci-avant, il devient un type Double ou String, selon le cas.</span><span class="sxs-lookup"><span data-stu-id="7d65c-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="7d65c-139">Les types Int16, UInt16, Int32, UInt32, Int64, UInt64, Single et Decimal deviennent un type Double.</span><span class="sxs-lookup"><span data-stu-id="7d65c-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="7d65c-140">Tous les autres types deviennent un type String à l'aide de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="7d65c-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="7d65c-141">Pour utiliser le paramètre XSLT, vous devez procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="7d65c-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="7d65c-142">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez les objets à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="7d65c-143">Appelez les paramètres à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="7d65c-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="7d65c-144">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7d65c-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d65c-145">Example</span></span>  

 <span data-ttu-id="7d65c-146">L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> pour créer un paramètre destiné à contenir une date de remise calculée.</span><span class="sxs-lookup"><span data-stu-id="7d65c-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="7d65c-147">La date de la remise correspond à 20 jours à partir de la date de la commande.</span><span class="sxs-lookup"><span data-stu-id="7d65c-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
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
  
### <a name="input"></a><span data-ttu-id="7d65c-148">Entrée</span><span class="sxs-lookup"><span data-stu-id="7d65c-148">Input</span></span>  

 <span data-ttu-id="7d65c-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="7d65c-149">order.xml</span></span>  
  
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
  
 <span data-ttu-id="7d65c-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="7d65c-150">discount.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="7d65c-151">Sortie</span><span class="sxs-lookup"><span data-stu-id="7d65c-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="7d65c-152">Objets d'extension XSLT</span><span class="sxs-lookup"><span data-stu-id="7d65c-152">XSLT Extension Objects</span></span>  

 <span data-ttu-id="7d65c-153">Des objets d’extension XSLT sont ajoutés à l’objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="7d65c-154">Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.</span><span class="sxs-lookup"><span data-stu-id="7d65c-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="7d65c-155">Lors de l'ajout d'un objet, l'appelant de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> doit être d'un niveau de confiance suffisant dans la stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7d65c-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="7d65c-156">Si l'appelant est d'un niveau de confiance partiel, l'ajout n'aboutira pas.</span><span class="sxs-lookup"><span data-stu-id="7d65c-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="7d65c-157">L'ajout correct d'un objet ne garantit pas le succès de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7d65c-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="7d65c-158">Lorsque la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est appelée, les autorisations sont calculées par rapport aux preuves fournies lors de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>, et ce jeu d'autorisations est attribué à l'ensemble du processus de transformation.</span><span class="sxs-lookup"><span data-stu-id="7d65c-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="7d65c-159">Si un objet d’extension tente d’initier une action qui nécessite des autorisations qui ne se trouvent pas dans le jeu, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="7d65c-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="7d65c-160">Les types de données retournés par les objets d’extension correspondent à l’un des quatre types de données de base XPath : nombre, chaîne, booléen et collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="7d65c-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="7d65c-161">Pour utiliser l’objet d’extension XSLT, vous devez procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="7d65c-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="7d65c-162">Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l’objet extension à l’aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="7d65c-163">Appelez l'objet d'extension à partir de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="7d65c-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="7d65c-164">Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d65c-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7d65c-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d65c-165">Example</span></span>  

 <span data-ttu-id="7d65c-166">L'exemple suivant calcule la circonférence d'un cercle en fonction de son rayon.</span><span class="sxs-lookup"><span data-stu-id="7d65c-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
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
  
### <a name="input"></a><span data-ttu-id="7d65c-167">Entrée</span><span class="sxs-lookup"><span data-stu-id="7d65c-167">Input</span></span>  

 <span data-ttu-id="7d65c-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="7d65c-168">number.xml</span></span>  
  
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
  
 <span data-ttu-id="7d65c-169">circle.xsl</span><span class="sxs-lookup"><span data-stu-id="7d65c-169">circle.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="7d65c-170">Sortie</span><span class="sxs-lookup"><span data-stu-id="7d65c-170">Output</span></span>  

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
  
## <a name="see-also"></a><span data-ttu-id="7d65c-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d65c-171">See also</span></span>

- [<span data-ttu-id="7d65c-172">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="7d65c-172">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
