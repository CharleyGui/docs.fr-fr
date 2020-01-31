---
title: System.Xml, utilisation
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 2ecb709684834a8280c841eb8eef4f024481f7a4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743583"
---
# <a name="systemxml-usage"></a>System.Xml, utilisation
Cette section parle de l’utilisation de plusieurs types résidant dans <xref:System.Xml?displayProperty=nameWithType> espaces de noms qui peuvent être utilisés pour représenter des données XML.

 ❌ n’utilisez pas <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> pour représenter des données XML. Privilégiez l’utilisation d’instances de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ou des sous-types de <xref:System.Xml.Linq.XNode> à la place. `XmlNode` et `XmlDocument` ne sont pas conçus pour être exposés dans des API publiques.

 ✔️ Utilisez `XmlReader`, `IXPathNavigable`ou des sous-types de `XNode` comme entrée ou sortie des membres qui acceptent ou retournent du code XML.

 Utilisez ces abstractions au lieu de `XmlDocument`, `XmlNode`ou <xref:System.Xml.XPath.XPathDocument>, car cela dissocie les méthodes des implémentations spécifiques d’un document XML en mémoire et les permet de travailler avec des sources de données XML virtuelles qui exposent `XNode`, `XmlReader`ou <xref:System.Xml.XPath.XPathNavigator>.

 ❌ ne sous-classez pas `XmlDocument` si vous souhaitez créer un type représentant une vue XML d’un modèle d’objet sous-jacent ou d’une source de données.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
