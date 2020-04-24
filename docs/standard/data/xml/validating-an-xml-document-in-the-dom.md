---
title: Validation d'un document XML dans le DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 93686ddf1afff76926e77acdbf5aa58e93d6cb77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710035"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Validation d'un document XML dans le DOM

La classe <xref:System.Xml.XmlDocument> ne valide pas le XML dans le DOM (Document Object Model) par rapport à un schéma de langage XSD (XML Schema Definition) ou à une définition de type de document (DTD) par défaut ; il est seulement vérifié que le XML est correctement construit.

Vous pouvez valider le XML lors de son chargement dans le DOM en transférant un objet <xref:System.Xml.XmlReader> de validation de schéma à la méthode <xref:System.Xml.XmlDocument.Load%2A> de la classe <xref:System.Xml.XmlDocument>, ou vous pouvez valider un document XML qui n'était pas validé dans le DOM à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Validation d'un document XML lors de son chargement dans le DOM

La classe <xref:System.Xml.XmlDocument> valide les données XML lors de leur chargement dans le DOM lorsqu'un objet <xref:System.Xml.XmlReader> de validation est transféré à la méthode <xref:System.Xml.XmlDocument.Load%2A> de la classe <xref:System.Xml.XmlDocument>.

Après une validation réussie, les valeurs par défaut du schéma sont appliquées, les valeurs texte sont converties au besoin en valeurs atomiques et les informations sur le type sont associées aux éléments d’information validés. Par conséquent, les données XML typées remplacent les données XML qui ne l'étaient pas.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Création d'un XmlReader de validation de schéma XML

Pour créer un objet <xref:System.Xml.XmlReader> de validation de schéma XML, procédez comme suit.

1. Construisez une nouvelle instance de l'objet <xref:System.Xml.XmlReaderSettings>.

2. Ajoutez un schéma XML à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> de l'instance de l'objet <xref:System.Xml.XmlReaderSettings>.

3. Spécifiez `Schema` en tant que propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.

4. Vous pouvez aussi spécifier la propriété <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> et <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> pour traiter les erreurs et les avertissements de validation de schéma détectés au cours de la validation.

5. Transférez enfin l'objet <xref:System.Xml.XmlReaderSettings> à la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> avec le document XML, créant ainsi un objet <xref:System.Xml.XmlReader> de validation de schéma.

### <a name="example"></a>Exemple

Dans l'exemple de code suivant, un objet <xref:System.Xml.XmlReader> de validation de schéma valide les données XML chargées dans le DOM. Des modifications non valides sont apportées au document XML, puis le document est revalidé, entraînant des erreurs de validation de schéma. Une des erreurs est finalement corrigée et une partie du document XML est ensuite partiellement validée.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

L'exemple prend le fichier `contosoBooks.xml` comme entrée.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Tenez compte des éléments suivants lors de la validation des données XML lors de leur chargement dans le DOM.

- Dans l'exemple ci-dessus, l'événement <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> est appelé chaque fois qu'un type non valide est rencontré. Si aucun événement <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> n'est défini sur l'objet <xref:System.Xml.XmlReader> de validation, une exception <xref:System.Xml.Schema.XmlSchemaValidationException> est levée quand <xref:System.Xml.XmlDocument.Load%2A> est appelé si un type d'attribut ou d'élément ne correspond pas au type spécifié dans le schéma de validation.

- Lorsqu'un document XML est chargé dans un objet <xref:System.Xml.XmlDocument> avec un schéma associé qui définit les valeurs par défaut, l'objet <xref:System.Xml.XmlDocument> traite ces valeurs par défaut comme si elles apparaissaient dans le document XML. Cela signifie que la propriété <xref:System.Xml.XmlReader.IsEmptyElement%2A> retourne toujours `false` pour un élément associé au schéma. Même s'il se trouvait dans le document XML, il était écrit comme un élément vide.

## <a name="validating-an-xml-document-in-the-dom"></a>Validation d'un document XML dans le DOM

La méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument> valide les données XML chargées dans le DOM par rapport aux schémas de la propriété <xref:System.Xml.XmlDocument>de l'objet <xref:System.Xml.XmlDocument.Schemas%2A>. Après une validation réussie, les valeurs par défaut du schéma sont appliquées, les valeurs texte sont converties au besoin en valeurs atomiques et les informations sur le type sont associées aux éléments d’information validés. Par conséquent, les données XML typées remplacent les données XML qui ne l'étaient pas.

L'exemple ci-dessous est similaire à celui se trouvant dans la section « Validation d'un document XML lors de son chargement dans le DOM » ci-dessus. Dans cet exemple, le document XML n'est pas validé lors de son chargement dans le DOM, mais bien après qu'il a été chargé dans le DOM à l'aide de la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>. La méthode <xref:System.Xml.XmlDocument.Validate%2A> valide le document XML par rapport aux schémas XML contenus dans la propriété <xref:System.Xml.XmlDocument.Schemas%2A> de l'objet <xref:System.Xml.XmlDocument>. Des modifications non valides sont alors apportées au document XML, puis le document est revalidé, entraînant des erreurs de validation de schéma. Une des erreurs est finalement corrigée et une partie du document XML est ensuite partiellement validée.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

L'exemple prend comme entrée les fichiers `contosoBooks.xml` et `contosoBooks.xsd` dont il est fait référence dans la section « Validation d'un document XML lors de son chargement dans le DOM » ci-dessus.

## <a name="handling-validation-errors-and-warnings"></a>Traitement des erreurs et avertissements de validation

Les erreurs de validation de schéma XML sont signalées lors de la validation des données XML chargées dans le DOM. Vous êtes notifié de toutes les erreurs de validation de schéma détectées lors de la validation des données XML en cours de chargement, ou lors de la validation d’un document XML qui n’était pas validé.

Les erreurs de validation sont traitées par l'objet <xref:System.Xml.Schema.ValidationEventHandler>. Si un objet <xref:System.Xml.Schema.ValidationEventHandler> a été assigné à l'instance de l'objet <xref:System.Xml.XmlReaderSettings> ou transféré à la méthode <xref:System.Xml.XmlDocument.Validate%2A> de la classe <xref:System.Xml.XmlDocument>, l'objet <xref:System.Xml.Schema.ValidationEventHandler> traitera les erreurs de validation de schéma ; sinon, un objet <xref:System.Xml.Schema.XmlSchemaValidationException> est levé lorsqu'une erreur de validation de schéma est détectée.

> [!NOTE]
> Les données XML sont chargées dans le DOM malgré des erreurs de validation de schéma à moins que votre objet <xref:System.Xml.Schema.ValidationEventHandler> soulève une exception afin d’arrêter le processus.
>
> Les avertissements de validation de schéma ne sont pas signalés à moins que l’indicateur <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> ne soit spécifié à l’objet <xref:System.Xml.XmlReaderSettings>.

 Pour obtenir des exemples illustrant l'objet <xref:System.Xml.Schema.ValidationEventHandler>, consultez les sections « Validation d'un document XML lors de son chargement dans le DOM » et « Validation d'un document XML dans le DOM » ci-dessus.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Traitement de données XML à l'aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Utilisation de schémas XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
