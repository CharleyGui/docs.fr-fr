---
title: Prise en charge du type dans les classes System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710100"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="4bf0d-102">Prise en charge du type dans les classes System.Xml</span><span class="sxs-lookup"><span data-stu-id="4bf0d-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="4bf0d-103">Dans .NET Framework version 2.0, les classes XML noyau ont été améliorées pour inclure des fonctions de prise en charge du type.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="4bf0d-104">Les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> comprennent des fonctionnalités de prise en charge du type, notamment la possibilité de conversion entre des types de schémas XML et des types CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4bf0d-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="4bf0d-105">Dans .NET Framework version 2.0, les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> ont été améliorées pour inclure des fonctionnalités de prise en charge du type.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="4bf0d-106">Les classes <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator> contiennent chacune une propriété **SchemaInfo** qui retourne les informations de schéma à un nœud.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="4bf0d-107">Les méthodes **ReadContentAs** et **ReadElementContentAs** de la classe <xref:System.Xml.XmlReader> lisent une valeur texte et la convertissent en valeur CLR en un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="4bf0d-108">La méthode <xref:System.Xml.XmlWriter.WriteValue%2A> de la classe <xref:System.Xml.XmlWriter> convertit un type CLR en type de schéma XML lors de l'écriture de XML.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="4bf0d-109">Les propriétés **ValueAs** et <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> retournent une valeur de nœud et la convertissent en valeur CLR en un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bf0d-110">Dans .NET Framework version 1.0, la classe <xref:System.Xml.XmlConvert> était nécessaire pour la conversion entre les types CLR et de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bf0d-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4bf0d-111">In This Section</span></span>  
 [<span data-ttu-id="4bf0d-112">Mappage entre types de données XML et types CLR</span><span class="sxs-lookup"><span data-stu-id="4bf0d-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="4bf0d-113">Décrit les mappages par défaut des types de données XML en types CLR.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="4bf0d-114">Remarques pour l'implémentation de la prise en charge du type XML</span><span class="sxs-lookup"><span data-stu-id="4bf0d-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="4bf0d-115">Explique certains détails de l'implémentation de la prise en charge du type.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="4bf0d-116">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="4bf0d-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="4bf0d-117">Décrit l'utilisation de la classe <xref:System.Xml.XmlConvert> pour la conversion entre des types CLR et de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="4bf0d-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4bf0d-118">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="4bf0d-118">Related Sections</span></span>  
 [<span data-ttu-id="4bf0d-119">Accès à des données XML fortement typées à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4bf0d-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
