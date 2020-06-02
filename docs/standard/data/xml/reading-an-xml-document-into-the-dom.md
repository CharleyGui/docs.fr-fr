---
title: Lecture d'un document XML dans le DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282400"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="f626b-102">Lecture d'un document XML dans le DOM</span><span class="sxs-lookup"><span data-stu-id="f626b-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="f626b-103">Les informations XML lues en mémoire peuvent être de différents formats :</span><span class="sxs-lookup"><span data-stu-id="f626b-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="f626b-104">chaîne, flux, URL, lecteur de texte ou classe dérivée de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="f626b-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="f626b-105">La méthode <xref:System.Xml.XmlDocument.Load%2A> charge le document en mémoire et des méthodes surchargées sont disponibles pour prendre des données de chacun des différents formats.</span><span class="sxs-lookup"><span data-stu-id="f626b-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="f626b-106">Il existe également une méthode <xref:System.Xml.XmlDocument.LoadXml%2A>, qui lit du XML à partir d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f626b-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="f626b-107">Les nœuds créés lors du chargement du DOM (Document Object Model) XML varient selon la méthode <xref:System.Xml.XmlDocument.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="f626b-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="f626b-108">Le tableau suivant répertorie les différences entre certaines des méthodes <xref:System.Xml.XmlDocument.Load%2A> et les rubriques où elles sont traitées.</span><span class="sxs-lookup"><span data-stu-id="f626b-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="f626b-109">Objet</span><span class="sxs-lookup"><span data-stu-id="f626b-109">Subject</span></span>|<span data-ttu-id="f626b-110">Rubrique</span><span class="sxs-lookup"><span data-stu-id="f626b-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="f626b-111">Création de nœuds d'espace blanc</span><span class="sxs-lookup"><span data-stu-id="f626b-111">Creation of white space nodes</span></span>|<span data-ttu-id="f626b-112">L'objet utilisé pour charger le DOM a un effet sur l'espace blanc et sur les nœuds d'espace blanc significatifs générés dans le DOM.</span><span class="sxs-lookup"><span data-stu-id="f626b-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="f626b-113">Pour plus d'informations, consultez [Gestion des espaces blancs significatifs ou non lors du chargement du DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="f626b-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="f626b-114">Chargement de XML à partir d'un nœud spécifique ou chargement du document XML entier</span><span class="sxs-lookup"><span data-stu-id="f626b-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="f626b-115">La méthode <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> permet de charger des données dans le DOM à partir d'un nœud spécifique.</span><span class="sxs-lookup"><span data-stu-id="f626b-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="f626b-116">Pour plus d’informations, consultez [Chargement de données à partir d’un lecteur](load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="f626b-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="f626b-117">Validation du XML lors de son chargement</span><span class="sxs-lookup"><span data-stu-id="f626b-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="f626b-118">Les données XML chargées dans le DOM peuvent être validées à mesure qu'elles sont chargées.</span><span class="sxs-lookup"><span data-stu-id="f626b-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="f626b-119">Utilisez pour cela un objet <xref:System.Xml.XmlReader> de validation.</span><span class="sxs-lookup"><span data-stu-id="f626b-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f626b-120">Pour plus d'informations sur la validation de XML lors de son chargement, voir [Validation d’un document XML dans le DOM](validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="f626b-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="f626b-121">L'exemple suivant montre le chargement de XML avec la méthode <xref:System.Xml.XmlDocument.LoadXml%2A> et l'enregistrement des données dans un fichier texte appelé `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="f626b-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f626b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f626b-122">See also</span></span>

- [<span data-ttu-id="f626b-123">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="f626b-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
