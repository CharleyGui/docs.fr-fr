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
# <a name="systemxml-usage"></a><span data-ttu-id="6dcef-102">System.Xml, utilisation</span><span class="sxs-lookup"><span data-stu-id="6dcef-102">System.Xml Usage</span></span>
<span data-ttu-id="6dcef-103">Cette section parle de l’utilisation de plusieurs types résidant dans <xref:System.Xml?displayProperty=nameWithType> espaces de noms qui peuvent être utilisés pour représenter des données XML.</span><span class="sxs-lookup"><span data-stu-id="6dcef-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="6dcef-104">❌ n’utilisez pas <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> pour représenter des données XML.</span><span class="sxs-lookup"><span data-stu-id="6dcef-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="6dcef-105">Privilégiez l’utilisation d’instances de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ou des sous-types de <xref:System.Xml.Linq.XNode> à la place.</span><span class="sxs-lookup"><span data-stu-id="6dcef-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="6dcef-106">`XmlNode` et `XmlDocument` ne sont pas conçus pour être exposés dans des API publiques.</span><span class="sxs-lookup"><span data-stu-id="6dcef-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="6dcef-107">✔️ Utilisez `XmlReader`, `IXPathNavigable`ou des sous-types de `XNode` comme entrée ou sortie des membres qui acceptent ou retournent du code XML.</span><span class="sxs-lookup"><span data-stu-id="6dcef-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="6dcef-108">Utilisez ces abstractions au lieu de `XmlDocument`, `XmlNode`ou <xref:System.Xml.XPath.XPathDocument>, car cela dissocie les méthodes des implémentations spécifiques d’un document XML en mémoire et les permet de travailler avec des sources de données XML virtuelles qui exposent `XNode`, `XmlReader`ou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6dcef-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="6dcef-109">❌ ne sous-classez pas `XmlDocument` si vous souhaitez créer un type représentant une vue XML d’un modèle d’objet sous-jacent ou d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="6dcef-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="6dcef-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6dcef-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6dcef-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6dcef-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6dcef-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dcef-112">See also</span></span>

- [<span data-ttu-id="6dcef-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6dcef-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6dcef-114">Indications relatives à l’utilisation</span><span class="sxs-lookup"><span data-stu-id="6dcef-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
