---
title: Sérialisation XML et SOAP
description: Cette vue d’ensemble décrit la sérialisation XML, qui peut être utilisée pour sérialiser des objets en flux XML conformes à la spécification SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: f7ad7732f929ac3599942c5440b173ea226cca87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544984"
---
# <a name="xml-and-soap-serialization"></a>Sérialisation XML et SOAP

La sérialisation XML convertit (sérialise) les champs et les propriétés publics d’un objet, ainsi que les paramètres et les valeurs de retour des méthodes, en un flux XML conforme à un document en langage XSD (XML Schema Definition) spécifique. La sérialisation XML permet d'obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format série (dans ce cas, XML) pour le stockage ou le transport.

XML étant une norme ouverte, le flux de données XML peut être traité si nécessaire par toute application, quelle que soit la plateforme. Par exemple, les services Web XML créés à l'aide d'ASP.NET utilisent la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML qui passent des données entre des applications de services Web XML sur Internet ou des intranets. Inversement, la désérialisation utilise le flux de données XML et reconstruit l'objet.

La sérialisation XML peut également être utilisée pour sérialiser des objets en flux XML se conformant à la spécification SOAP. SOAP est un protocole basé sur XML, conçu spécifiquement pour transporter des appels de procédure à l'aide de XML.

Pour sérialiser ou désérialiser des objets, utilisez la classe <xref:System.Xml.Serialization.XmlSerializer>. Pour créer les classes à sérialiser, utilisez l'outil XML Schema Definition.

## <a name="see-also"></a>Voir aussi

- [Sérialisation binaire](binary-serialization.md)
- [Services Web XML créés à l’aide des clients de service Web XML et ASP.NET](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
