---
title: Traitement de données XML en mémoire
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 06863d162a9f9fbf67f41cb12ea4fbb1935b424d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291277"
---
# <a name="processing-xml-data-in-memory"></a>Traitement de données XML en mémoire
Microsoft .NET Framework comprend trois modèles pour le traitement des données XML : la classe <xref:System.Xml.XmlDocument>, la classe <xref:System.Xml.XPath.XPathDocument>, [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) et [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 La classe <xref:System.Xml.XmlDocument> implémente les recommandations du W3C relatives aux modèles objet de document (DOM), niveaux 1 et 2 (noyau). Le DOM est une représentation sous la forme d'une arborescence (cache) en mémoire d'un document XML. L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et d'enregistrer des modifications.  
  
 La classe <xref:System.Xml.XPath.XPathDocument> est un magasin de données en mémoire en lecture seule basé sur le modèle de données XPath. La classe <xref:System.Xml.XPath.XPathNavigator> propose plusieurs options de modification et fonctionnalités de navigation à l'aide d'un modèle de curseur entre des documents XML contenus dans la classe <xref:System.Xml.XPath.XPathDocument> en lecture seule ainsi que dans la classe <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) est un modèle introduit dans .NET Framework version 3.5 pour le traitement des données XML. Il s’agit d’un modèle en mémoire qui tire parti de [LINQ (Language-Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ étend la syntaxe des langages C# et Visual Basic pour fournir de nouvelles capacités de requête.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Traitement de données XML à l'aide du modèle DOM](process-xml-data-using-the-dom-model.md)  
 Explique l'utilisation de l'objet <xref:System.Xml.XmlDocument> et des classes y afférentes pour le traitement de données XML.  
  
 [Traitement des données XML à l'aide du modèle de données XPath](process-xml-data-using-the-xpath-data-model.md)  
 Explique l'utilisation des classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> et <xref:System.Xml.XPath.XPathNavigator> pour le traitement de données XML.  
  
 [Traitement des données XML à l'aide de LINQ to XML](process-xml-data-using-linq-to-xml.md)  
 Fournit une brève vue d'ensemble de LINQ to XML et indique des liens vers la documentation LINQ to XML.  
  
## <a name="related-sections"></a>Sections connexes  
 [Documents et données XML](index.md)
