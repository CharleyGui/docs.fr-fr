---
title: Vue d’ensemble des classes LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591883"
---
# <a name="linq-to-xml-classes-overview-c"></a>Vue d’ensemble des classes LINQ to XML (C#)
Cette rubrique fournit une liste des classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans l'espace de noms <xref:System.Xml.Linq> et une brève description de chacune d'entre elles.  
  
## <a name="linq-to-xml-classes"></a>Classes LINQ to XML  
  
### <a name="xattribute-class"></a>Classe XAttribute  
 <xref:System.Xml.Linq.XAttribute> représente un attribut XML. Pour des informations détaillées et des exemples, consultez [Vue d’ensemble de la classe XAttribute (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Classe XCData  
 <xref:System.Xml.Linq.XCData> représente un nœud de texte CDATA.  
  
### <a name="xcomment-class"></a>Classe XComment  
 <xref:System.Xml.Linq.XComment> représente un commentaire XML.  
  
### <a name="xcontainer-class"></a>Classe XContainer  
 <xref:System.Xml.Linq.XContainer> est une classe de base abstraite pour tous les nœuds pouvant comporter des nœuds enfants. Les classes suivantes dérivent de la classe <xref:System.Xml.Linq.XContainer> :  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Classe XDeclaration  
 <xref:System.Xml.Linq.XDeclaration> représente une déclaration XML. Une déclaration XML est utilisée pour déclarer la version XML et l'encodage d'un document. Une déclaration XML spécifie également si le document XML est autonome. Si un document est autonome, il n'existe aucune déclaration de marque externe, que ce soit dans un DTD externe ou dans une entité de paramètre externe référencée à partir du sous-ensemble interne.  
  
### <a name="xdocument-class"></a>Classe XDocument  
 <xref:System.Xml.Linq.XDocument> représente un document XML. Pour des informations détaillées et des exemples, consultez [Vue d’ensemble de la classe XDocument (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Classe XDocumentType  
 <xref:System.Xml.Linq.XDocumentType> représente une définition DTD (Document Type Definition) XML.  
  
### <a name="xelement-class"></a>Classe XElement  
 <xref:System.Xml.Linq.XElement> représente un élément XML. Pour des informations détaillées et des exemples, consultez [Vue d’ensemble de la classe XElement (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>Classe XName  
 <xref:System.Xml.Linq.XName> représente des noms d'éléments (<xref:System.Xml.Linq.XElement>) et d'attributs (<xref:System.Xml.Linq.XAttribute>). Pour des informations détaillées et des exemples, consultez [Vue d’ensemble de la classe XDocument (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est conçu pour rendre les noms XML aussi simples que possible. En raison de leur complexité, les noms XML sont souvent considérés comme l'un des aspects les plus difficiles à appréhender du langage XML. En fait, cette complexité provient non pas des espaces de noms, que les développeurs utilisent régulièrement dans la programmation, mais des préfixes d'espaces de noms. Les préfixes d'espaces de noms peuvent être utiles pour réduire le nombre de frappes au clavier nécessaires lors de la saisie de code XML ou pour améliorer la lisibilité du code XML. Toutefois, les préfixes sont souvent simplement un raccourci pour l'ensemble de l'espace de noms XML, et ils ne sont pas nécessaires dans la plupart des cas. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] simplifie les noms XML en résolvant tous les préfixes en leur espace de noms XML correspondant. Les préfixes sont disponibles, si besoin, via la méthode <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>.  
  
 Il est possible, si nécessaire, de contrôler les préfixes d'espaces de noms. Dans certains cas, si vous travaillez avec d'autres systèmes XML, tels que XSLT ou XAML, vous devez contrôler les préfixes d'espaces de noms. Par exemple, si vous avez une expression XPath qui utilise des préfixes d'espaces de noms et qui est incorporée dans une feuille de style XSLT, vous devez vous assurer que votre document XML est sérialisé avec des préfixes d'espaces de noms qui correspondent à ceux utilisés dans l'expression XPath.  
  
### <a name="xnamespace-class"></a>Classe XNamespace  
 <xref:System.Xml.Linq.XNamespace> représente un espace de noms pour un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>. Les espaces de noms sont un composant d'un objet <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Classe XNode  
 <xref:System.Xml.Linq.XNode> est une classe abstraite qui représente les nœuds d'une arborescence XML. Les classes suivantes dérivent de la classe <xref:System.Xml.Linq.XNode> :  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Classe XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> fournit la fonctionnalité permettant de comparer des nœuds pour ce qui est de l'ordre des documents.  
  
### <a name="xnodeequalitycomparer-class"></a>Classe XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer> fournit la fonctionnalité permettant de comparer des nœuds pour ce qui est de l'égalité des valeurs.  
  
### <a name="xobject-class"></a>Classe XObject  
 <xref:System.Xml.Linq.XObject> est une classe de base abstraite de <xref:System.Xml.Linq.XNode> et <xref:System.Xml.Linq.XAttribute>. Elle fournit des fonctionnalités d'annotation et d'événement.  
  
### <a name="xobjectchange-class"></a>Classe XObjectChange  
 <xref:System.Xml.Linq.XObjectChange> spécifie le type d'événement lorsqu'un événement est déclenché pour un objet <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>Classe XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> fournit des données pour les événements <xref:System.Xml.Linq.XObject.Changing> et <xref:System.Xml.Linq.XObject.Changed>.  
  
### <a name="xprocessinginstruction-class"></a>Classe XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction> représente une instruction de traitement XML. Une instruction de traitement communique des informations à une application qui traite le code XML.  
  
### <a name="xtext-class"></a>Classe XText  
 <xref:System.Xml.Linq.XText> représente un nœud de texte. Dans la plupart des cas, il est inutile d'utiliser cette classe. Cette classe est utilisée principalement pour du contenu mixte.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation LINQ to XML (C#)](./linq-to-xml-overview.md)
