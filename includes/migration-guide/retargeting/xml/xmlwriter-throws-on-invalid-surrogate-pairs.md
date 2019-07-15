---
ms.openlocfilehash: b7f31060fd845f7618479fd064350b3cb5532fd3
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804540"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a>XmlWriter lève une exception en cas de paires de substitution non valides

|   |   |
|---|---|
|Détails|Pour les applications qui ciblent .NET Framework 4.5.2 ou des versions antérieures, l'écriture d'une paire de substitution non valide à l'aide de la gestion des stratégies de secours des exceptions ne lève pas toujours une exception. Pour les applications qui ciblent le .NET Framework 4.6, la tentative d’écriture d’une paire de substitution non valide lève une exception <xref:System.ArgumentException?displayProperty=name>.|
|Suggestion|Si nécessaire, vous pouvez éviter cette interruption en ciblant le .NET Framework 4.5.2 ou antérieur. Vous pouvez également prétraiter les paires de substitution non valides en code XML valide avant de les écrire.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType></li></ul>|

