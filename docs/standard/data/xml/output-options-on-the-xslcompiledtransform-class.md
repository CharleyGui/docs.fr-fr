---
title: Options de sortie de la classe XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: e9ffdc1377dbf124f042802279e7e7a275222eff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288704"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Options de sortie de la classe XslCompiledTransform
Cette rubrique présente les options de sortie XSLT disponibles. Vous pouvez spécifier des options de sortie dans la feuille de style ou dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="xsloutput-element"></a>Élément xsl:output  
 L'élément `xsl:output` spécifie des options de sortie. Le type de sortie spécifié par la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> détermine le comportement des options `xsl:output`.  
  
 Le tableau suivant décrit le comportement de chacun des attributs disponibles dans l'élément `xsl:output` lorsque le type de sortie est un flux ou un objet <xref:System.IO.TextWriter>.  
  
|Nom de l’attribut|Comportement|  
|--------------------|--------------|  
|method|Pris en charge.|  
|version|Ignoré. La version est toujours 1.0 pour XML et 4.0 pour HTML.|  
|encodage|Ignoré en cas de sortie vers un objet <xref:System.IO.TextWriter>. La propriété <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> est utilisée à la place.|  
|omit-xml-declaration|Pris en charge.|  
|autonomes|Pris en charge.|  
|doctype-public|Pris en charge.|  
|doctype-system|Pris en charge.|  
|cdata-section-elements|Pris en charge.|  
|indent|Pris en charge.|  
|media-type|Pris en charge.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Envoi de la sortie vers un XmlWriter  
 Si votre feuille de style utilise l'élément `xsl:output` et que le type de sortie est un objet <xref:System.Xml.XmlWriter>, utilisez la propriété <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> lorsque vous créez l'objet <xref:System.Xml.XmlWriter>. La propriété <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> retourne un objet <xref:System.Xml.XmlWriterSettings> contenant des informations dérivées de l'élément `xsl:output` d'une feuille de style compilée. Cet objet <xref:System.Xml.XmlWriterSettings> peut être transféré à la méthode <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> pour créer un objet <xref:System.Xml.XmlWriter> avec les paramètres corrects.  
  
## <a name="output-types"></a>Types de sortie  
 La liste suivante décrit les types de sortie disponibles avec la commande <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
#### <a name="xmlwriter"></a>XmlWriter  
 La classe <xref:System.Xml.XmlWriter> produit des fichiers ou des flux XML. Vous pouvez spécifier les fonctionnalités à prendre en charge dans l’objet <xref:System.Xml.XmlWriter>, y compris les options de sortie, en utilisant la classe <xref:System.Xml.XmlWriterSettings>. La classe <xref:System.Xml.XmlWriter> fait partie intégrante de l'infrastructure <xref:System.Xml>. Utilisez ce type de sortie pour envoyer les résultats vers un autre processus XML via un pipeline.  
  
#### <a name="string"></a>String  
 Utilisez ce type de sortie pour spécifier l'URI du fichier de sortie.  
  
#### <a name="stream"></a>Flux  
 Un flux est une abstraction d'une séquence d'octets, comme un fichier, un appareil d'entrée/sortie, un canal de communication inter-processus ou un socket TCP/IP. La classe <xref:System.IO.Stream> et ses classes dérivées donnent une vue générique de ces différents types d'entrée et de sortie, isolant ainsi le programmeur des détails propres au système d'exploitation et aux périphériques sous-jacents.  
  
 Utilisez ce type de sortie pour envoyer des données à un objet <xref:System.IO.FileStream>, à un objet <xref:System.IO.MemoryStream> ou à un flux de sortie (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 L'objet <xref:System.IO.TextWriter> produit des caractères séquentiels. Il est implémenté dans les classes <xref:System.IO.StringWriter> et <xref:System.IO.StreamWriter>, qui écrivent des caractères dans des chaînes ou des flux, respectivement. Utilisez ce type de sortie lorsque vous souhaitez envoyer la sortie vers une chaîne.  
  
## <a name="notes"></a>Notes  
  
- Lorsque vous écrivez des chaînes vides, un espace est inséré entre le dernier caractère du nom de l'élément et la barre oblique inverse, par exemple `<myElement />`. Cela permet aux anciens navigateurs d'afficher correctement les pages HTML générées.  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](xslt-transformations.md)
