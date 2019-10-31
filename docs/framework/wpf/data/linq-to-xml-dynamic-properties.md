---
title: Référence des propriétés dynamiques LINQ to XML
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 48b51e92eb78786b2cc189e3e7daa00875b41585
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197050"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="b6859-102">Propriétés dynamiques LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b6859-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="b6859-103">Cette section fournit des informations de référence sur les propriétés dynamiques dans LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b6859-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="b6859-104">Plus spécifiquement, ces propriétés sont exposées par les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont dans l'espace de noms <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="b6859-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="b6859-105">Comme expliqué dans la rubrique [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), chacune des propriétés dynamiques est équivalente à une méthode ou propriété publique standard dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="b6859-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="b6859-106">Ces membres standard doivent être utilisés dans la plupart des cas ; des propriétés dynamiques sont fournies spécifiquement pour les scénarios de liaison de données LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b6859-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="b6859-107">Pour plus d'informations sur les membres standard de ces classes, consultez les rubriques de référence <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b6859-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="b6859-108">En ce qui concerne leurs valeurs résolues, les propriétés dynamiques dans cette section se répartissent en deux catégories :</span><span class="sxs-lookup"><span data-stu-id="b6859-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="b6859-109">Les propriétés simples, telles que les propriétés `Value` dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont résolues à une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="b6859-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="b6859-110">Les valeurs indexées, telles que les propriétés [Elements](elements-xelement-dynamic-property.md) et [Descendants](descendants-xelement-dynamic-property.md) de l’objet <xref:System.Xml.Linq.XElement>, qui sont résolues en un type d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="b6859-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="b6859-111">Pour que les types d’indexeur soient résolus à la valeur ou collection souhaitée, un paramètre de nom étendu doit leur être passé.</span><span class="sxs-lookup"><span data-stu-id="b6859-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="b6859-112">Toutes les propriétés dynamiques qui retournent une valeur indexée de type <xref:System.Collections.Generic.IEnumerable%601> utilisent l’exécution différée.</span><span class="sxs-lookup"><span data-stu-id="b6859-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="b6859-113">Pour plus d’informations sur l’exécution différée, consultez [Introduction aux requêtes LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b6859-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="reference"></a><span data-ttu-id="b6859-114">Reference</span><span class="sxs-lookup"><span data-stu-id="b6859-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="b6859-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6859-115">See also</span></span>

- [<span data-ttu-id="b6859-116">Liaison de données WPF avec LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b6859-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="b6859-117">Vue d’ensemble de la liaison de données WPF avec LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b6859-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="b6859-118">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b6859-118">Introduction to LINQ queries (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
