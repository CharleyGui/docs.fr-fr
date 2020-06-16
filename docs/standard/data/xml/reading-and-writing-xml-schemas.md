---
title: Lecture et écriture de schémas XML
description: Lire et écrire des schémas en langage XSD (XML Schema Definition) à partir de fichiers ou d’autres sources dans .NET, à l’aide de l’API SOM (Schema Object Model).
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 874b0bdb0e13d545cfff4c813881f1398a8f9487
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767661"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="ce561-103">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-103">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="ce561-104">L’API Modèle Objet du schéma (SOM) peut permettre de lire et écrire des schémas de langage XSD (XML Schema Definition) dans des fichiers ou d’autres sources et de générer un cache de schéma XML à l’aide des classes de l’espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> correspondant aux structures définies dans la recommandation du W3C (World Wide Web Consortium) sur les schémas XML.</span><span class="sxs-lookup"><span data-stu-id="ce561-104">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="ce561-105">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-105">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="ce561-106">La classe <xref:System.Xml.Schema.XmlSchema> fournit les méthodes <xref:System.Xml.Schema.XmlSchema.Read%2A> et <xref:System.Xml.Schema.XmlSchema.Write%2A> pour lire et écrire des schémas XML.</span><span class="sxs-lookup"><span data-stu-id="ce561-106">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="ce561-107">La méthode <xref:System.Xml.Schema.XmlSchema.Read%2A> retourne un objet <xref:System.Xml.Schema.XmlSchema> représentant le schéma XML et prend un objet <xref:System.Xml.Schema.ValidationEventHandler> facultatif comme paramètre pour traiter les avertissements et erreurs de validation de schéma rencontrées lors de la lecture d'un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="ce561-107">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="ce561-108">La méthode <xref:System.Xml.Schema.XmlSchema.Write%2A> écrit des schémas XML dans des objets <xref:System.IO.Stream>, <xref:System.IO.TextWriter> et <xref:System.Xml.XmlWriter> et peut prendre un <xref:System.Xml.XmlNamespaceManager> facultatif comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="ce561-108">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="ce561-109">Un objet <xref:System.Xml.XmlNamespaceManager> permet de traiter les espaces de noms rencontrés dans un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="ce561-109">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="ce561-110">Pour plus d’informations sur la classe <xref:System.Xml.XmlNamespaceManager>, consultez [Gestion d’espaces de noms dans un document XML](managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ce561-110">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="ce561-111">L'exemple de code suivant illustre la lecture et l'écriture de schémas XML à partir de et vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="ce561-111">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="ce561-112">Il prend le fichier `example.xsd`, le lit dans un objet <xref:System.Xml.Schema.XmlSchema> à l'aide de la méthode `static`<xref:System.Xml.Schema.XmlSchema.Read%2A>, puis l'écrit dans la console et dans un nouveau fichier `new.xsd`.</span><span class="sxs-lookup"><span data-stu-id="ce561-112">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="ce561-113">Il fournit également un objet <xref:System.Xml.Schema.ValidationEventHandler> comme paramètre à la méthode `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> pour traiter les avertissements ou erreurs de validation de schéma rencontrés pendant la lecture du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="ce561-113">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="ce561-114">Si l'objet <xref:System.Xml.Schema.ValidationEventHandler> n'est pas spécifié (`null`), aucun avertissement ou aucune erreur n'est signalée.</span><span class="sxs-lookup"><span data-stu-id="ce561-114">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="ce561-115">L'exemple prend le fichier `example.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="ce561-115">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce561-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce561-116">See also</span></span>

- [<span data-ttu-id="ce561-117">Vue d'ensemble du Modèle Objet du schéma XML</span><span class="sxs-lookup"><span data-stu-id="ce561-117">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="ce561-118">Création de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-118">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="ce561-119">Traversée de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-119">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="ce561-120">Modification de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-120">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="ce561-121">Inclusion ou importation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="ce561-121">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="ce561-122">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="ce561-122">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="ce561-123">Jeu d'informations de post-compilation de schéma</span><span class="sxs-lookup"><span data-stu-id="ce561-123">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="ce561-124">Gestion d'espaces de noms dans un document XML</span><span class="sxs-lookup"><span data-stu-id="ce561-124">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
