---
title: Conservation des espaces blancs lors de la sérialisation3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 2f1e59728dc353a86421c9071710aba23c8f7f6f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608730"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="110a6-102">Conservation des espaces blancs lors de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="110a6-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="110a6-103">Cette rubrique décrit comment contrôler les espaces blancs lors de la sérialisation d'une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="110a6-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="110a6-104">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="110a6-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="110a6-105">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="110a6-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="110a6-106">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="110a6-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="110a6-107">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="110a6-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="110a6-108">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="110a6-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="110a6-109">Pour ce faire dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="110a6-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="110a6-110">Gestion des espaces blancs par les méthodes qui sérialisent des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="110a6-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="110a6-111">Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> sérialisent une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="110a6-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="110a6-112">Vous pouvez sérialiser une arborescence XML vers un fichier, un objet <xref:System.IO.TextReader> ou un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="110a6-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="110a6-113">La méthode `ToString` sérialise vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="110a6-113">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="110a6-114">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="110a6-114">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="110a6-115">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="110a6-115">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="110a6-116">Si la méthode ne prend pas l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, elle mettra en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="110a6-116">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="110a6-117">Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.</span><span class="sxs-lookup"><span data-stu-id="110a6-117">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="110a6-118">Si la méthode prend l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, vous pouvez spécifier qu'elle ne mettra pas en forme (en retrait) le code XML sérialisé.</span><span class="sxs-lookup"><span data-stu-id="110a6-118">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="110a6-119">Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.</span><span class="sxs-lookup"><span data-stu-id="110a6-119">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110a6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="110a6-120">See also</span></span>

- [<span data-ttu-id="110a6-121">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="110a6-121">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
