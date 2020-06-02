---
title: System.Xml, utilisation
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291667"
---
# <a name="systemxml-usage"></a>System.Xml, utilisation
Cette section parle de l’utilisation de plusieurs types résidant dans des <xref:System.Xml?displayProperty=nameWithType> espaces de noms qui peuvent être utilisés pour représenter des données XML.

 ❌N’utilisez pas <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> pour représenter des données XML. Privilégiez l’utilisation d’instances de <xref:System.Xml.XPath.IXPathNavigable> ,, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> ou de sous-types de à la <xref:System.Xml.Linq.XNode> place. `XmlNode`et ne `XmlDocument` sont pas conçus pour être exposés dans des API publiques.

 ✔️ Utilisez `XmlReader` `IXPathNavigable` les sous-types, ou `XNode` en tant qu’entrée ou sortie des membres qui acceptent ou retournent du code XML.

 Utilisez ces abstractions au lieu de `XmlDocument` , `XmlNode` ou <xref:System.Xml.XPath.XPathDocument> , car cela dissocie les méthodes des implémentations spécifiques d’un document XML en mémoire et leur permet de fonctionner avec des sources de données XML virtuelles qui exposent `XNode` , `XmlReader` ou <xref:System.Xml.XPath.XPathNavigator> .

 ❌Ne procédez pas `XmlDocument` à la sous-classe si vous souhaitez créer un type représentant une vue XML d’un modèle objet ou d’une source de données sous-jacent.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’utilisation](usage-guidelines.md)
