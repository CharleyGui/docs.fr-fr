---
title: Annotations LINQ to XML3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689944"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="6290b-102">Annotations LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="6290b-102">LINQ to XML Annotations</span></span>

<span data-ttu-id="6290b-103">Les annotations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6290b-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="6290b-104">Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>.</span><span class="sxs-lookup"><span data-stu-id="6290b-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="6290b-105">Vous pouvez récupérer des annotations par type.</span><span class="sxs-lookup"><span data-stu-id="6290b-105">You retrieve annotations by type.</span></span>

<span data-ttu-id="6290b-106">Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="6290b-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="6290b-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6290b-107">Methods</span></span>

<span data-ttu-id="6290b-108">Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :</span><span class="sxs-lookup"><span data-stu-id="6290b-108">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="6290b-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="6290b-109">Method</span></span>|<span data-ttu-id="6290b-110">Description</span><span class="sxs-lookup"><span data-stu-id="6290b-110">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="6290b-111">Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6290b-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="6290b-112">Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6290b-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="6290b-113">Obtient une collection d’annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6290b-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="6290b-114">Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6290b-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
