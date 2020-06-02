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
# <a name="reading-an-xml-document-into-the-dom"></a>Lecture d'un document XML dans le DOM
Les informations XML lues en mémoire peuvent être de différents formats : chaîne, flux, URL, lecteur de texte ou classe dérivée de l'objet <xref:System.Xml.XmlReader>.  
  
 La méthode <xref:System.Xml.XmlDocument.Load%2A> charge le document en mémoire et des méthodes surchargées sont disponibles pour prendre des données de chacun des différents formats. Il existe également une méthode <xref:System.Xml.XmlDocument.LoadXml%2A>, qui lit du XML à partir d'une chaîne.  
  
 Les nœuds créés lors du chargement du DOM (Document Object Model) XML varient selon la méthode <xref:System.Xml.XmlDocument.Load%2A>. Le tableau suivant répertorie les différences entre certaines des méthodes <xref:System.Xml.XmlDocument.Load%2A> et les rubriques où elles sont traitées.  
  
|Objet|Rubrique|  
|-------------|-----------|  
|Création de nœuds d'espace blanc|L'objet utilisé pour charger le DOM a un effet sur l'espace blanc et sur les nœuds d'espace blanc significatifs générés dans le DOM. Pour plus d'informations, consultez [Gestion des espaces blancs significatifs ou non lors du chargement du DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Chargement de XML à partir d'un nœud spécifique ou chargement du document XML entier|La méthode <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> permet de charger des données dans le DOM à partir d'un nœud spécifique. Pour plus d’informations, consultez [Chargement de données à partir d’un lecteur](load-data-from-a-reader.md).|  
|Validation du XML lors de son chargement|Les données XML chargées dans le DOM peuvent être validées à mesure qu'elles sont chargées. Utilisez pour cela un objet <xref:System.Xml.XmlReader> de validation. Pour plus d'informations sur la validation de XML lors de son chargement, voir [Validation d’un document XML dans le DOM](validating-an-xml-document-in-the-dom.md).|  
  
 L'exemple suivant montre le chargement de XML avec la méthode <xref:System.Xml.XmlDocument.LoadXml%2A> et l'enregistrement des données dans un fichier texte appelé `data.xml`.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
