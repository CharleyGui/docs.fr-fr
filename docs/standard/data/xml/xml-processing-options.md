---
title: Options de traitement XML
description: Passez en revue les options de traitement XML, notamment LINQ to XML, XmlReader, XmlWriter, XmlDocument, XPathNavigator, XslCompiledTransform, XmlLite et MSXML.
ms.date: 03/30/2017
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
ms.openlocfilehash: a0b3c6295874e891c1271b373fb012b5f191bcfb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829399"
---
# <a name="xml-processing-options"></a>Options de traitement XML
Reportez-vous aux tableaux suivants pour obtenir une liste des technologies Microsoft que vous pouvez utiliser pour traiter des données XML.  
  
## <a name="net-framework-options"></a>Options du .NET Framework  
  
|**Option**|**Type de traitement**|**Description**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML (C#)](../../linq/linq-xml-overview.md) <br/> [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) <br />(espace de noms <xref:System.Xml.Linq>)|En mémoire|-   Basé sur la technologie LINQ (Langage-Integrated Query) du .NET Framework.<br />-   Fournit une expérience de requête similaire à SQL pour les objets, les données relationnelles et les données XML.<br />-   Fournit des fonctionnalités de création et de transformation de documents intuitives.<br />-   Utilisez cette option si vous écrivez un nouveau code.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Basé sur les flux|-   Fournit un accès rapide, en avant seulement et non mis en cache aux données XML.<br />-   Vous pouvez créer des objets à l’aide de la méthode <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> et spécifier l’ensemble de fonctionnalités à activer sur l’objet avec la classe <xref:System.Xml.XmlReaderSettings>.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Basé sur les flux|-   Fournit un moyen rapide, en avant seulement et non mis en cache de générer des données XML.<br />-   Vous pouvez créer des objets à l’aide de la méthode <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> et spécifier l’ensemble de fonctionnalités à activer sur l’objet avec la classe <xref:System.Xml.XmlWriterSettings>.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|En mémoire|-   Implémente les recommandations du [W3C relatives aux modèles objet de document (DOM), niveaux 1](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) et [2 (noyau)](https://www.w3.org/TR/DOM-Level-2-Core/).<br />-   Vous pouvez créer, insérer, supprimer et modifier des nœuds à l'aide de méthodes et de propriétés basées sur le modèle DOM habituel.<br />-   Utilisez cette option si vous modifiez du code existant qui implémente le modèle W3C DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|En mémoire|-   Offre plusieurs options d'édition et capacités de navigation utilisant un modèle de curseur.<br />-   Les documents XML peuvent être contenus dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.<br />-   Procure d'excellentes performances pour le traitement en lecture seule du code XML.<br />-   Utilisez cette option si vous modifiez du code existant à l’aide de requêtes XPath ou de transformations XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|En mémoire|-   Fournit des options pour la transformation de données XML à l'aide des transformations XSL.<br />-   [XSLT Compiler (xsltc.exe)](xslt-compiler-xsltc-exe.md) vous permet de faire référence à des transformations précompilées dans votre application.|  
  
## <a name="win32-and-com-based-options"></a>Options Win32 et COM  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|[XmlLite](/previous-versions/windows/desktop/ms752872(v=vs.85))|-   Analyseur XML rapide, sécurisé, sans mise en cache et avant uniquement qui vous permet de créer des applications XML hautes performances.<br />-   Fonctionne avec n'importe quel langage capable d'utiliser des bibliothèques de liens dynamiques (DLL). Nous recommandons l'utilisation de C++.|  
|[MSXML](/previous-versions/windows/desktop/ms763742(v=vs.85))|-   Technologie compatible COM pour le traitement du code XML, qui est fournie avec le système d'exploitation Windows.<br />-   Fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT.<br />-   Inclut l'analyseur basé sur les événements SAX2.|  
  
## <a name="see-also"></a>Voir aussi

- [Traitement de données XML à l'aide du modèle DOM](process-xml-data-using-the-dom-model.md)
- [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)
- [XSLT Compiler (xsltc.exe)](xslt-compiler-xsltc-exe.md)
