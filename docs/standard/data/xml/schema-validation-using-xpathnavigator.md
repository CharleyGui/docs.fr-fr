---
title: Validation de schéma à l'aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: bfcbf7306e896af54808c49e25f95d0631f5bcc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710204"
---
# <a name="schema-validation-using-xpathnavigator"></a>Validation de schéma à l'aide de XPathNavigator
La classe <xref:System.Xml.XmlDocument> permet de valider le contenu XML d'un objet <xref:System.Xml.XmlDocument> de deux manières. La première consiste à valider le contenu XML à l'aide d'un objet <xref:System.Xml.XmlReader> de validation et la seconde, à utiliser la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>. Vous pouvez également effectuer une validation en lecture seule du contenu XML à l’aide de la classe <xref:System.Xml.XPath.XPathDocument>.  
  
## <a name="validating-xml-data"></a>Validation de données XML  
 La classe <xref:System.Xml.XmlDocument> ne valide pas de document XML à l’aide d’une DTD ou d’une validation de schéma de langage XSD (XML schema definition) par défaut. Elle vérifie uniquement que le document XML est correctement construit.  
  
 La première manière de valider un document XML consiste à valider le document lors de son chargement dans un objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation. La seconde consiste à valider un document XML précédemment non typé à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>. Dans les deux cas, toute modification apportée au document XML validé peut être revalidée à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Validation d'un document lors de son chargement  
 Un objet <xref:System.Xml.XmlReader> de validation est créé par la transmission d'un objet <xref:System.Xml.XmlReaderSettings> à la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> qui prend un objet <xref:System.Xml.XmlReaderSettings> comme paramètre. L'objet <xref:System.Xml.XmlReaderSettings> transmis sous la forme d'un paramètre possède une propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> définie sur `Schema` et un schéma XML pour le document XML contenu dans l'objet <xref:System.Xml.XmlDocument> ajouté à sa propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A>. L'objet <xref:System.Xml.XmlReader> de validation permet ensuite de créer l'objet <xref:System.Xml.XmlDocument>.  
  
 L'exemple suivant valide le fichier `contosoBooks.xml` lors de son chargement dans l'objet <xref:System.Xml.XmlDocument> en créant l'objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation. Comme le document XML est valide par rapport à son schéma, aucun avertissement ou aucune erreur de validation de schéma n’est générée.  
  
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
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Dans l'exemple ci-dessus, une <xref:System.Xml.Schema.XmlSchemaValidationException> est levée quand <xref:System.Xml.XmlDocument.Load%2A> est appelé si un type d'attribut ou d'élément ne correspond pas au type spécifié dans le schéma de validation. Si un <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> est défini sur la <xref:System.Xml.XmlReader> de validation, le <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> est appelé chaque fois qu'un type non valide est rencontré.  
  
 Une <xref:System.Xml.Schema.XmlSchemaException> est levée si le <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> accède à un attribut ou à un élément dont le `invalid` est défini sur <xref:System.Xml.XPath.XPathNavigator>.  
  
 La propriété <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> peut être utilisée pour déterminer si un attribut ou un élément est valide ou non lors de l'accès aux attributs ou éléments avec le <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> Lorsqu'un document XML est chargé dans un objet <xref:System.Xml.XmlDocument> avec un schéma associé qui définit les valeurs par défaut, l'objet <xref:System.Xml.XmlDocument> traite ces valeurs par défaut comme si elles apparaissaient dans le document XML. Ceci signifie que la propriété <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> retourne toujours `false` pour un élément dont la valeur par défaut provenait du schéma, même s'il était écrit comme élément vide dans le document XML.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Validation d'un document à l'aide de la méthode Validate  
 La méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument> valide le document XML contenu dans un objet <xref:System.Xml.XmlDocument> par rapport aux schémas spécifiés dans la propriété <xref:System.Xml.XmlDocument> de l'objet <xref:System.Xml.XmlDocument.Schemas%2A> et effectue une augmentation infoset. En guise de résultat, un document XML précédemment non typé dans l'objet <xref:System.Xml.XmlDocument> est remplacé par un document typé.  
  
 L’objet <xref:System.Xml.XmlDocument> signale des avertissements et des erreurs de validation de schéma à l’aide du délégué <xref:System.Xml.Schema.ValidationEventHandler> transmis sous la forme d’un paramètre à la méthode <xref:System.Xml.XmlDocument.Validate%2A>.  
  
 L'exemple suivant valide le fichier `contosoBooks.xml` contenu dans l'objet <xref:System.Xml.XmlDocument> par rapport au schéma `contosoBooks.xsd` contenu dans la propriété <xref:System.Xml.XmlDocument> de l'objet <xref:System.Xml.XmlDocument.Schemas%2A>.  
  
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
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Validation de modifications  
 Une fois que vous avez modifié un document XML, vous pouvez valider les modifications par rapport au schéma pour le document XML à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.  
  
 L'exemple suivant valide le fichier `contosoBooks.xml` lors de son chargement dans l'objet <xref:System.Xml.XmlDocument> en créant l'objet <xref:System.Xml.XmlDocument> à l'aide d'un objet <xref:System.Xml.XmlReader> de validation. Le document XML est correctement validé lors de son chargement et aucun avertissement ou aucune erreur de validation de schéma n’est générée. L'exemple apporte ensuite deux modifications au document XML non valides par rapport au schéma `contosoBooks.xsd`. La première modification insère un élément enfant non valide, provoquant une erreur de validation de schéma et la deuxième modification définit la valeur d’un nœud typé sur une valeur non valide par rapport au type de nœud, provoquant une erreur.  
  
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
  
 L'exemple prend le fichier `contosoBooks.xml` comme entrée.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Dans l'exemple ci-dessus, deux modifications sont apportées au document XML contenu dans l'objet <xref:System.Xml.XmlDocument>. Lors du chargement du document XML, toute erreur de validation de schéma rencontrée doit avoir été traitée par la méthode du gestionnaire d'événements de validation et écrite dans la console.  
  
 Dans cet exemple, les erreurs de validation ont été introduites après le chargement du document XML et trouvées à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.  
  
 Les modifications apportées à l'aide de la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> ont généré une <xref:System.InvalidCastException> car la nouvelle valeur était non valide par rapport au type de schéma du nœud.  
  
 Pour plus d’informations sur la modification de valeurs avec la méthode <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, consultez la rubrique [Modification de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md).  
  
### <a name="read-only-validation"></a>Validation en lecture seule  
 La classe <xref:System.Xml.XPath.XPathDocument> est une représentation en lecture seule et en mémoire d'un document XML. Les classes <xref:System.Xml.XPath.XPathDocument> et <xref:System.Xml.XmlDocument> créent des objets <xref:System.Xml.XPath.XPathNavigator> permettant de parcourir et de modifier des documents XML. Étant donné que la classe <xref:System.Xml.XPath.XPathDocument> est une classe en lecture seule, l'objet <xref:System.Xml.XPath.XPathNavigator> retourné par les objets <xref:System.Xml.XPath.XPathDocument> ne peut pas modifier le document XML contenu dans l'objet <xref:System.Xml.XPath.XPathDocument>.  
  
 En cas de validation, vous pouvez créer un objet <xref:System.Xml.XPath.XPathDocument> de la même manière qu’un objet <xref:System.Xml.XmlDocument> à l’aide d’un objet <xref:System.Xml.XmlReader> de validation comme décrit précédemment dans cette rubrique. L'objet <xref:System.Xml.XPath.XPathDocument> valide le document XML lors de son chargement, mais comme vous ne pouvez pas modifier les données XML dans l'objet <xref:System.Xml.XPath.XPathDocument>, vous ne pouvez pas revalider le document XML.  
  
 Pour plus d’informations sur les objets <xref:System.Xml.XPath.XPathNavigator> en lecture seule et modifiables, consultez la rubrique [Lecture de données XML à l’aide de XPathDocument et de XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Lecture de données XML à l’aide de XPathDocument et XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Accès à des données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Modification de données XML à l'aide de XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
