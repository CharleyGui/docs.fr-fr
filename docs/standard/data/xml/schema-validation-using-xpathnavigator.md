---
title: Validation de schéma à l'aide de XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: 1c91dfa63723cc087662630232376e74394c7b13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734697"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="6c0c3-102">Validation de schéma à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c0c3-102">Schema Validation using XPathNavigator</span></span>

<span data-ttu-id="6c0c3-103">La classe <xref:System.Xml.XmlDocument> permet de valider le contenu XML d'un objet <xref:System.Xml.XmlDocument> de deux manières.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="6c0c3-104">La première consiste à valider le contenu XML à l'aide d'un objet <xref:System.Xml.XmlReader> de validation et la seconde, à utiliser la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="6c0c3-105">Vous pouvez également effectuer une validation en lecture seule du contenu XML à l’aide de la classe <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="6c0c3-106">Validation de données XML</span><span class="sxs-lookup"><span data-stu-id="6c0c3-106">Validating XML Data</span></span>  

 <span data-ttu-id="6c0c3-107">La classe <xref:System.Xml.XmlDocument> ne valide pas de document XML à l’aide d’une DTD ou d’une validation de schéma de langage XSD (XML schema definition) par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="6c0c3-108">Elle vérifie uniquement que le document XML est correctement construit.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="6c0c3-109">La première manière de valider un document XML consiste à valider le document lors de son chargement dans un objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6c0c3-110">La seconde consiste à valider un document XML précédemment non typé à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="6c0c3-111">Dans les deux cas, toute modification apportée au document XML validé peut être revalidée à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="6c0c3-112">Validation d'un document lors de son chargement</span><span class="sxs-lookup"><span data-stu-id="6c0c3-112">Validating a Document as it is Loaded</span></span>  

 <span data-ttu-id="6c0c3-113">Un objet <xref:System.Xml.XmlReader> de validation est créé par la transmission d'un objet <xref:System.Xml.XmlReaderSettings> à la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> qui prend un objet <xref:System.Xml.XmlReaderSettings> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="6c0c3-114">L'objet <xref:System.Xml.XmlReaderSettings> transmis sous la forme d'un paramètre possède une propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> définie sur `Schema` et un schéma XML pour le document XML contenu dans l'objet <xref:System.Xml.XmlDocument> ajouté à sa propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="6c0c3-115">L'objet <xref:System.Xml.XmlReader> de validation permet ensuite de créer l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="6c0c3-116">L'exemple suivant valide le fichier `contosoBooks.xml` lors de son chargement dans l'objet <xref:System.Xml.XmlDocument> en créant l'objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6c0c3-117">Comme le document XML est valide par rapport à son schéma, aucun avertissement ou aucune erreur de validation de schéma n’est générée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6c0c3-118">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="6c0c3-119">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="6c0c3-120">Dans l'exemple ci-dessus, une <xref:System.Xml.Schema.XmlSchemaValidationException> est levée quand <xref:System.Xml.XmlDocument.Load%2A> est appelé si un type d'attribut ou d'élément ne correspond pas au type spécifié dans le schéma de validation.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="6c0c3-121">Si un <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> est défini sur la <xref:System.Xml.XmlReader> de validation, le <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> est appelé chaque fois qu'un type non valide est rencontré.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="6c0c3-122">Une <xref:System.Xml.Schema.XmlSchemaException> est levée si le <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> accède à un attribut ou à un élément dont le `invalid` est défini sur <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="6c0c3-123">La propriété <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> peut être utilisée pour déterminer si un attribut ou un élément est valide ou non lors de l'accès aux attributs ou éléments avec le <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c0c3-124">Lorsqu'un document XML est chargé dans un objet <xref:System.Xml.XmlDocument> avec un schéma associé qui définit les valeurs par défaut, l'objet <xref:System.Xml.XmlDocument> traite ces valeurs par défaut comme si elles apparaissaient dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="6c0c3-125">Ceci signifie que la propriété <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> retourne toujours `false` pour un élément dont la valeur par défaut provenait du schéma, même s'il était écrit comme élément vide dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="6c0c3-126">Validation d'un document à l'aide de la méthode Validate</span><span class="sxs-lookup"><span data-stu-id="6c0c3-126">Validating a Document using the Validate Method</span></span>  

 <span data-ttu-id="6c0c3-127">La méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument> valide le document XML contenu dans un objet <xref:System.Xml.XmlDocument> par rapport aux schémas spécifiés dans la propriété <xref:System.Xml.XmlDocument> de l'objet <xref:System.Xml.XmlDocument.Schemas%2A> et effectue une augmentation infoset.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="6c0c3-128">En guise de résultat, un document XML précédemment non typé dans l'objet <xref:System.Xml.XmlDocument> est remplacé par un document typé.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="6c0c3-129">L’objet <xref:System.Xml.XmlDocument> signale des avertissements et des erreurs de validation de schéma à l’aide du délégué <xref:System.Xml.Schema.ValidationEventHandler> transmis sous la forme d’un paramètre à la méthode <xref:System.Xml.XmlDocument.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="6c0c3-130">L'exemple suivant valide le fichier `contosoBooks.xml` contenu dans l'objet <xref:System.Xml.XmlDocument> par rapport au schéma `contosoBooks.xsd` contenu dans la propriété <xref:System.Xml.XmlDocument> de l'objet <xref:System.Xml.XmlDocument.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6c0c3-131">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="6c0c3-132">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="6c0c3-133">Validation de modifications</span><span class="sxs-lookup"><span data-stu-id="6c0c3-133">Validating Modifications</span></span>  

 <span data-ttu-id="6c0c3-134">Une fois que vous avez modifié un document XML, vous pouvez valider les modifications par rapport au schéma pour le document XML à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="6c0c3-135">L'exemple suivant valide le fichier `contosoBooks.xml` lors de son chargement dans l'objet <xref:System.Xml.XmlDocument> en créant l'objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6c0c3-136">Le document XML est correctement validé lors de son chargement et aucun avertissement ou aucune erreur de validation de schéma n’est générée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="6c0c3-137">L'exemple apporte ensuite deux modifications au document XML non valides par rapport au schéma `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="6c0c3-138">La première modification insère un élément enfant non valide, provoquant une erreur de validation de schéma et la deuxième modification définit la valeur d’un nœud typé sur une valeur non valide par rapport au type de nœud, provoquant une erreur.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="6c0c3-139">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="6c0c3-140">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="6c0c3-141">Dans l'exemple ci-dessus, deux modifications sont apportées au document XML contenu dans l'objet <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="6c0c3-142">Lors du chargement du document XML, toute erreur de validation de schéma rencontrée doit avoir été traitée par la méthode du gestionnaire d'événements de validation et écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="6c0c3-143">Dans cet exemple, les erreurs de validation ont été introduites après le chargement du document XML et trouvées à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="6c0c3-144">Les modifications apportées à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> ont généré une <xref:System.InvalidCastException> car la nouvelle valeur était non valide par rapport au type de schéma du nœud.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="6c0c3-145">Pour plus d’informations sur la modification de valeurs avec la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c3-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="6c0c3-146">Validation en lecture seule</span><span class="sxs-lookup"><span data-stu-id="6c0c3-146">Read-Only Validation</span></span>  

 <span data-ttu-id="6c0c3-147">La classe <xref:System.Xml.XPath.XPathDocument> est une représentation en lecture seule et en mémoire d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="6c0c3-148">Les classes <xref:System.Xml.XPath.XPathDocument> et <xref:System.Xml.XmlDocument> créent des objets <xref:System.Xml.XPath.XPathNavigator> permettant de parcourir et de modifier des documents XML.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="6c0c3-149">Étant donné que la classe <xref:System.Xml.XPath.XPathDocument> est une classe en lecture seule, l'objet <xref:System.Xml.XPath.XPathNavigator> retourné par les objets <xref:System.Xml.XPath.XPathDocument> ne peut pas modifier le document XML contenu dans l'objet <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="6c0c3-150">En cas de validation, vous pouvez créer un objet <xref:System.Xml.XPath.XPathDocument> de la même manière qu’un objet <xref:System.Xml.XmlDocument> à l’aide d’un objet <xref:System.Xml.XmlReader> de validation comme décrit précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="6c0c3-151">L'objet <xref:System.Xml.XPath.XPathDocument> valide le document XML lors de son chargement, mais comme vous ne pouvez pas modifier les données XML dans l'objet <xref:System.Xml.XPath.XPathDocument>, vous ne pouvez pas revalider le document XML.</span><span class="sxs-lookup"><span data-stu-id="6c0c3-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="6c0c3-152">Pour plus d’informations sur les objets <xref:System.Xml.XPath.XPathNavigator> en lecture seule et modifiables, consultez la rubrique [Lecture de données XML à l’aide de XPathDocument et de XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c3-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0c3-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c0c3-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="6c0c3-154">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="6c0c3-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="6c0c3-155">Lecture de données XML à l’aide de XPathDocument et XmlDocument</span><span class="sxs-lookup"><span data-stu-id="6c0c3-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="6c0c3-156">Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c0c3-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6c0c3-157">Accès à des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c0c3-157">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6c0c3-158">Modification de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c0c3-158">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
