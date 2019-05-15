---
title: Vue d'ensemble du Modèle Objet du schéma XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97e2e54c534b30c3c514c9102ded0050fc154b75
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589789"
---
# <a name="xml-schema-object-model-overview"></a>Vue d'ensemble du Modèle Objet du schéma XML
Le Modèle Objet du schéma (SOM) de Microsoft .NET Framework est une API riche permettant de créer, modifier et valider des schémas à l'aide d'un programme. Le SOM travaille sur des documents de schéma XML de la même manière que le DOM (Document Object Model) travaille sur des documents XML. Les documents de schéma XML sont des fichiers XML valides qui, une fois chargés dans le SOM, communiquent la signification de la structure et de la validité d'autres documents XML conformes au schéma.  
  
 Un schéma est un document XML qui définit une classe de documents XML en spécifiant la structure ou le modèle de documents XML pour un schéma particulier. Un schéma identifie les contraintes de contenu des documents XML et décrit le vocabulaire (règles ou grammaire) que les documents XML conformes doivent respecter pour être considérés comme valides par rapport au schéma dans ce schéma particulier. La validation d’un document XML est le processus qui garantit que le document respecte la grammaire spécifiée par le schéma.  
  
 Les opérations suivantes de l'API du SOM de .NET Framework permettent de créer, modifier et valider des schémas.  
  
- Chargement et enregistrement de schémas valides dans et à partir de fichiers  
  
- Création de schémas en mémoire à l'aide de classes fortement typées  
  
- Interactions avec la classe <xref:System.Xml.Schema.XmlSchemaSet> pour mettre en cache, compiler et récupérer des schémas  
  
- Interactions avec la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> pour valider des documents d'instance XML par rapport à des schémas  
  
- Génération d'éditeurs pour la création et la gestion de schémas  
  
- Modification dynamique d'un schéma pouvant être respectée et enregistrée pour une utilisation dans la validation de documents d'instance XML  
  
## <a name="the-schema-object-model"></a>Modèle Objet du schéma  
 Le SOM se compose d'un ensemble extensible de classe dans l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> correspondant aux éléments d'un schéma XML. Par exemple, l'élément `<xsd:schema>...</xsd:schema>` correspond à la classe <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> et toutes les informations pouvant être contenues dans un élément `<xsd:schema/>` peuvent être représentées à l'aide de la classe <xref:System.Xml.Schema.XmlSchema>. De même, les éléments `<xsd:element>...</xsd:element>` et `<xsd:attribute>...</xsd:attribute>` correspondent respectivement aux classes <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> et <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType>. Cette correspondance continue pour tous les éléments d'un schéma XML via la création d'un modèle d'objet de schéma XML dans l'espace de noms <xref:System.Xml.Schema> illustré dans le diagramme suivant.  
  
 ![Modèle objet System.Xml.Schema](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 Pour plus d'informations sur chaque classe de l'espace de noms <xref:System.Xml.Schema>, voir la documentation de référence sur l'espace de noms <xref:System.Xml.Schema> dans la bibliothèque de classes de .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [Lecture et écriture de schémas XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Création de schémas XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Parcours des schémas XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Modification de schémas XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Inclusion ou importation de schémas XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Infoset de post-compilation de schéma](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
