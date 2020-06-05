---
title: "Comment : charger du code XML à partir d'un fichier, d'une chaîne ou d'un flux"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392286"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Comment : charger du code XML à partir d'un fichier, d'une chaîne ou d'un flux (Visual Basic)

Vous pouvez créer des [littéraux XML](../../../language-reference/xml-literals/index.md) et les remplir avec le contenu d’une source externe, telle qu’un fichier, une chaîne ou un flux à l’aide de plusieurs méthodes. Ces méthodes sont illustrées dans les exemples suivants.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Pour charger du code XML à partir d’un fichier

Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’un fichier, utilisez la `Load` méthode. Cette méthode peut accepter un chemin d’accès de fichier, un flux de texte ou un flux XML comme entrée.

L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Load%28System.String%29> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’un fichier texte.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Pour charger du code XML à partir d’une chaîne

Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’une chaîne, vous pouvez utiliser la `Parse` méthode.

L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’une chaîne.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Pour charger du code XML à partir d’un flux

Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou à partir d’un flux, vous pouvez utiliser la `Load` méthode ou la <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> méthode.

L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XNode.ReadFrom%2A> méthode pour remplir un <xref:System.Xml.Linq.XDocument> objet avec du code XML à partir d’un flux XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Littéraux XML](../../../language-reference/xml-literals/index.md)
- [XML](index.md)
- [Manipulation de code XML dans Visual Basic](manipulating-xml.md)
