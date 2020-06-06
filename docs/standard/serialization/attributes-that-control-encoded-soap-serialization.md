---
title: Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP
description: Cet article répertorie un ensemble spécial d’attributs trouvés dans l’espace de noms System. Xml. Serialization requis pour se conformer à la spécification SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: d9a4631189d348c02ab36054257a54c9c4673018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289666"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP

Le document World Wide Web Consortium (W3C) nommé [simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contient une section facultative (section 5) qui décrit comment les paramètres SOAP peuvent être encodés. Pour se conformer à la section 5 de la spécification, vous devez utiliser un ensemble spécial d’attributs figurant dans l’espace de noms <xref:System.Xml.Serialization>. Appliquez ces attributs en fonction des classes et membres de classes, puis utilisez <xref:System.Xml.Serialization.XmlSerializer> pour sérialiser les instances de la ou des classes.

Le tableau suivant affiche les attributs, leurs conditions d'application et l'action qu'ils entraînent. Pour plus d’informations sur l’utilisation de ces attributs pour contrôler la sérialisation XML, consultez [Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) et [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](how-to-override-encoded-soap-xml-serialization.md).

Pour plus d’informations sur les attributs, consultez [Attributs](../attributes/index.md).

|Attribut|S’applique à|Spécifie|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Champ public, propriété, paramètre ou valeur de retour.|Le membre de classe est sérialisé en tant qu'attribut XML.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|Champ public, propriété, paramètre ou valeur de retour.|La classe est sérialisée en tant qu'élément XML.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Champ public qui est un identificateur d'énumération.|Nom d'élément d'un membre d'énumération.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Champs et propriétés publics.|La propriété ou le champ doit être ignoré lorsque la classe conteneur est sérialisée.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Déclarations de classe dérivée publiques et méthodes publiques pour les documents WSDL (Web Services Description Language).|Le type doit être inclus lors de la génération de schémas (afin d'être reconnu en cas de sérialisation).|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Déclarations de classe publiques.|La classe doit être sérialisée en tant que type XML.|

## <a name="see-also"></a>Voir aussi

- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](how-to-override-encoded-soap-xml-serialization.md)
- [Attributs](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md)
