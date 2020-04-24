---
title: Implémentation du processeur XSLT par la classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: 73a432db9a3fcb6587184e27e6dfe9ba49010e92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709606"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="d3e2b-102">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="d3e2b-103">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="d3e2b-104">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d3e2b-105">Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2b-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="d3e2b-106">La classe <xref:System.Xml.Xsl.XslTransform> est un processeur XSLT qui implémente la recommandation XSL Transformations (XSLT) version 1.0.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="d3e2b-107">La méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> localise et lit des feuilles de style, et la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> transforme le document source donné.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="d3e2b-108">Tout magasin implémentant l'interface <xref:System.Xml.XPath.IXPathNavigable> peut être utilisé comme document source pour l'objet <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="d3e2b-109">Le .NET Framework implémente actuellement l’interface <xref:System.Xml.XPath.IXPathNavigable> sur les éléments <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument> et <xref:System.Xml.XPath.XPathDocument>, de sorte qu’ils peuvent tous être utilisés comme le document source d’entrée d’une transformation.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="d3e2b-110">L’objet <xref:System.Xml.Xsl.XslTransform> du .NET Framework prend uniquement en charge la spécification XSLT 1.0, définie par l’espace de noms suivant :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="d3e2b-111">La feuille de style peut être chargée, à l'aide de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>, à partir de l'une des classes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="d3e2b-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d3e2b-112">XPathNavigator</span></span>

- <span data-ttu-id="d3e2b-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="d3e2b-113">XmlReader</span></span>

- <span data-ttu-id="d3e2b-114">Une chaîne représentant une URL</span><span class="sxs-lookup"><span data-stu-id="d3e2b-114">A string representing a URL</span></span>

<span data-ttu-id="d3e2b-115">Il existe une méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> différente pour chacune des classes d'entrée ci-avant.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="d3e2b-116">Certaines méthodes prennent une combinaison de ces classes et la classe <xref:System.Xml.XmlResolver> comme arguments.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="d3e2b-117">L'objet <xref:System.Xml.XmlResolver> localise les ressources référencées par `<xsl:import>` ou `<xsl:include>` trouvées dans la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="d3e2b-118">Les méthodes suivantes prennent une chaîne, l'objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator>, comme entrée.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

<span data-ttu-id="d3e2b-119">La plupart des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> illustrées ci-avant prennent un objet <xref:System.Xml.XmlResolver> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="d3e2b-120">L'objet <xref:System.Xml.XmlResolver> s'utilise pour charger la feuille de style et toutes les feuilles de style référencées dans les éléments xsl:import et xsl:include.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="d3e2b-121">La plupart des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> prennent également la preuve comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="d3e2b-122">Le paramètre de preuve correspond à l'objet <xref:System.Security.Policy.Evidence> associé à la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="d3e2b-123">Le niveau de sécurité de la feuille de style affecte le niveau de sécurité de toutes les ressources ultérieures qu'elle référence, comme le script qu'elle contient, toute fonction `document()` qu'elle utilise, et tous les objets d'extension utilisés par l'objet <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="d3e2b-124">Si la feuille de style est chargée à l'aide de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> qui contient un paramètre d'URL et aucune preuve, la preuve de la feuille de style est calculée en combinant l'URL donnée avec son site et sa zone.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="d3e2b-125">Si aucun URI ou aucune preuve n'est fourni, la preuve définie pour la feuille de style est d'un niveau de confiance suffisant.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="d3e2b-126">Ne chargez pas de feuilles de style à partir de sources non fiables ou n'ajoutez pas d'objets d'extension non fiables dans l'objet <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="d3e2b-127">Pour plus d'informations sur les niveaux de sécurité et les preuves, ainsi que sur la manière dont ils affectent la création de scripts, consultez [XSLT Stylesheet Scripting à l’aide de \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2b-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="d3e2b-128">Pour plus d’informations sur les niveaux de sécurité et les preuves, ainsi que sur la manière dont ils affectent les objets d’extension, consultez [XsltArgumentList pour les paramètres de feuille de style et les objets d’extension](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2b-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="d3e2b-129">Pour plus d'informations sur les niveaux de sécurité et les preuves, ainsi que la manière dont ceux-ci affectent la fonction `document()`, consultez [Résolution de feuilles de style XSLT externes et de documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2b-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="d3e2b-130">Une feuille de style peut être fournie par un nombre de paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="d3e2b-131">La feuille de style peut également appeler des fonctions sur des objets d'extension.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="d3e2b-132">Tant les paramètres que les objets d'extension sont fournis à la feuille de style à l'aide de la classe <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="d3e2b-133">Pour plus d'informations sur le <xref:System.Xml.Xsl.XsltArgumentList>, consultez <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="d3e2b-134">Utilisation sécurisée recommandée de la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="d3e2b-135">Les privilèges de sécurité de la feuille de style dépendent de la preuve fournie.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="d3e2b-136">Le tableau suivant résume l'emplacement de la feuille de style et donne une explication du type de preuve à fournir.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="d3e2b-137">La feuille de style XSLT n'a pas de référence externe ou la feuille de style provient d'une base de code auquel vous faites confiance.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="d3e2b-138">Fournissez la preuve à partir de votre assembly :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="d3e2b-139">La feuille de style XSLT provient d'une source externe.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d3e2b-140">L'origine de la source est connue et il existe un URI vérifiable.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="d3e2b-141">Créez la preuve à l'aide de l'URI.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="d3e2b-142">La feuille de style XSLT provient d'une source externe.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d3e2b-143">L'origine de la source n'est pas connue.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="d3e2b-144">Attribuez à la preuve la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-144">Set evidence to `null`.</span></span> <span data-ttu-id="d3e2b-145">Les blocs de script ne sont pas traités, la fonction `document()` XSLT n’est pas prise en charge et les objets d’extension privilégiés ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="d3e2b-146">En outre, vous pouvez également attribuer la valeur `resolver` au paramètre `null`. Vous garantissez ainsi que les éléments `xsl:import` et `xsl:include` ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="d3e2b-147">La feuille de style XSLT provient d'une source externe.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d3e2b-148">L'origine de la source n'est pas connue, mais vous avez besoin de la prise en charge des scripts.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="d3e2b-149">Demandez une preuve à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="d3e2b-150">Transformation de données XML</span><span class="sxs-lookup"><span data-stu-id="d3e2b-150">Transformation of XML Data</span></span>

<span data-ttu-id="d3e2b-151">Dès qu'une feuille de style est chargée, la transformation démarre en appelant l'une des méthodes <xref:System.Xml.Xsl.XslTransform.Transform%2A> et en fournissant un document source d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="d3e2b-152">La méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est surchargée pour fournir diverses sorties de transformation.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="d3e2b-153">La transformation peut avoir comme résultat l'un des formats de sortie suivants :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="d3e2b-154">String URL de fichier</span><span class="sxs-lookup"><span data-stu-id="d3e2b-154">String URL of file</span></span>

<span data-ttu-id="d3e2b-155">Le dernier format (String URL) prévoit un scénario généralement utilisé consistant à transformer un document d'entrée situé dans une URL et à écrire le document dans l'URL de sortie.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="d3e2b-156">Cette méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est une méthode pratique pour charger un document XML à partir d'un fichier, effectuer la transformation XSLT et écrire la sortie dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="d3e2b-157">Il n'est donc pas nécessaire de créer et de charger le document source d'entrée, puis d'écrire dans un flux de fichier.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="d3e2b-158">L'exemple de code suivant illustre l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> utilisant le String URL en tant qu'entrée et sortie :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="d3e2b-159">Transformation d'une section d'un document XML</span><span class="sxs-lookup"><span data-stu-id="d3e2b-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="d3e2b-160">Les transformations s'appliquent à l'ensemble du document.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="d3e2b-161">En d'autres termes, si vous passez dans un autre nœud que le nœud racine du document, cela n'empêche pas le processus de transformation d'accéder à tous les nœuds dans le document chargé.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="d3e2b-162">Pour transformer un fragment d’arbre résultat, vous devez créer un objet <xref:System.Xml.XmlDocument> contenant uniquement le fragment d’arbre résultat et passer l’objet <xref:System.Xml.XmlDocument> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d3e2b-163">L’exemple suivant effectue une transformation sur un fragment d’arbre résultat.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-163">The following example performs a transformation on a result tree fragment.</span></span>

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

<span data-ttu-id="d3e2b-164">L’exemple utilise les fichiers Library. xml et print_root. xsl comme entrée et génère le résultat suivant sur la console :</span><span class="sxs-lookup"><span data-stu-id="d3e2b-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="d3e2b-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="d3e2b-165">library.xml</span></span>

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

<span data-ttu-id="d3e2b-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="d3e2b-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="d3e2b-167">Migration de XSLT depuis le .NET Framework version 1.0 vers le .NET Framework version 1.1</span><span class="sxs-lookup"><span data-stu-id="d3e2b-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="d3e2b-168">Le tableau suivant montre les méthodes obsolètes de .NET Framework version 1.0 et les nouvelles méthodes de .NET Framework version 1.1 pour la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="d3e2b-169">Les nouvelles méthodes vous permettent de limiter les autorisations de la feuille de style en spécifiant une preuve.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="d3e2b-170">Méthodes Load obsolètes du .NET Framework version 1.0</span><span class="sxs-lookup"><span data-stu-id="d3e2b-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="d3e2b-171">Méthodes Load de remplacement du .NET Framework version 1.1</span><span class="sxs-lookup"><span data-stu-id="d3e2b-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="d3e2b-172">Load(entrée XPathNavigator)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="d3e2b-173">Load(entrée XPathNavigator, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="d3e2b-174">Load(feuille de style XPathNavigator, programme de résolution XmlResolver, preuve Evidence)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="d3e2b-175">Load(feuille de style IXPathNavigable)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="d3e2b-176">Load(feuille de style IXPathNavigable, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d3e2b-177">Load(feuille de style IXPathNavigable, programme de résolution XmlResolver, preuve Evidence)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="d3e2b-178">Load(feuille de style XmlReader)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="d3e2b-179">Load(feuille de style XmlReader, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d3e2b-180">Load(feuille de style XmlReader, programme de résolution XmlResolver, preuve Evidence)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="d3e2b-181">Le tableau suivant illustre les méthodes obsolètes et nouvelles pour la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d3e2b-182">Les nouvelles méthodes prennent un objet <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="d3e2b-183">Méthodes Transform obsolètes du .NET Framework version 1.0</span><span class="sxs-lookup"><span data-stu-id="d3e2b-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="d3e2b-184">Méthodes Transform de remplacement du .NET Framework version 1.1</span><span class="sxs-lookup"><span data-stu-id="d3e2b-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="d3e2b-185">XmlReader Transform(entrée XPathNavigator, argument XsltArgumentList)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="d3e2b-186">XmlReader Transform(entrée XPathNavigator, argument XsltArgumentList, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-187">XmlReader Transform(entrée IXPathNavigable, argument XsltArgumentList)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="d3e2b-188">XmlReader Transform(entrée IXPathNavigable, argument XsltArgumentList, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-189">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d3e2b-190">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie XmlWriter, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-191">Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d3e2b-192">Void Transform(entrée IXpathNavigable, argument XsltArgumentList, sortie XmlWriter, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-193">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie TextWriter)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d3e2b-194">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie TextWriter, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-195">Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie TextWriter)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d3e2b-196">Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie TextWriter, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-197">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie Stream)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d3e2b-198">Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie Stream, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-199">Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie Stream)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d3e2b-200">Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie Stream, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="d3e2b-201">Void Transform(entrée String, sortie String)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="d3e2b-202">Void Transform(entrée String, sortie String, programme de résolution XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="d3e2b-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="d3e2b-203">La propriété <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> est obsolète dans .NET Framework version 1.1.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="d3e2b-204">Utilisez à la place les nouvelles surcharges <xref:System.Xml.Xsl.XslTransform.Transform%2A> qui acceptent un objet <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="d3e2b-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3e2b-205">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e2b-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="d3e2b-206">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="d3e2b-207">XPathNavigator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="d3e2b-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="d3e2b-208">XPathNodeIterator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="d3e2b-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="d3e2b-209">Entrée XPathDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="d3e2b-210">Entrée XmlDataDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="d3e2b-211">Entrée XmlDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="d3e2b-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
