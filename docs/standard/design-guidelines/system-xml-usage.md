---
title: System.Xml, utilisation
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 46282afa6548c731b04c40d8de91a1fed997c57c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677568"
---
# <a name="systemxml-usage"></a><span data-ttu-id="1f931-102">System.Xml, utilisation</span><span class="sxs-lookup"><span data-stu-id="1f931-102">System.Xml Usage</span></span>

<span data-ttu-id="1f931-103">Cette section parle de l’utilisation de plusieurs types résidant dans des <xref:System.Xml?displayProperty=nameWithType> espaces de noms qui peuvent être utilisés pour représenter des données XML.</span><span class="sxs-lookup"><span data-stu-id="1f931-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="1f931-104">❌ N’utilisez pas <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> pour représenter des données XML.</span><span class="sxs-lookup"><span data-stu-id="1f931-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="1f931-105">Privilégiez l’utilisation d’instances de <xref:System.Xml.XPath.IXPathNavigable> ,, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> ou de sous-types de à la <xref:System.Xml.Linq.XNode> place.</span><span class="sxs-lookup"><span data-stu-id="1f931-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="1f931-106">`XmlNode` et ne `XmlDocument` sont pas conçus pour être exposés dans des API publiques.</span><span class="sxs-lookup"><span data-stu-id="1f931-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="1f931-107">✔️ Utilisez `XmlReader` `IXPathNavigable` les sous-types, ou `XNode` en tant qu’entrée ou sortie des membres qui acceptent ou retournent du code XML.</span><span class="sxs-lookup"><span data-stu-id="1f931-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="1f931-108">Utilisez ces abstractions au lieu de `XmlDocument` , `XmlNode` ou <xref:System.Xml.XPath.XPathDocument> , car cela dissocie les méthodes des implémentations spécifiques d’un document XML en mémoire et leur permet de fonctionner avec des sources de données XML virtuelles qui exposent `XNode` , `XmlReader` ou <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="1f931-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="1f931-109">❌ Ne procédez pas `XmlDocument` à la sous-classe si vous souhaitez créer un type représentant une vue XML d’un modèle objet ou d’une source de données sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="1f931-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="1f931-110">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="1f931-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1f931-111">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1f931-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1f931-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f931-112">See also</span></span>

- [<span data-ttu-id="1f931-113">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="1f931-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1f931-114">Instructions d’utilisation</span><span class="sxs-lookup"><span data-stu-id="1f931-114">Usage Guidelines</span></span>](usage-guidelines.md)
