---
title: Annotations-LINQ to XML
description: Apprenez à utiliser des annotations dans LINQ to XML pour associer tout objet arbitraire de tout type arbitraire à n’importe quel composant XML dans une arborescence XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553367"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a><span data-ttu-id="f7d7c-103">Annotations de LINQ to XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f7d7c-103">LINQ to XML annotations (LINQ to XML)</span></span>

<span data-ttu-id="f7d7c-104">Les annotations dans LINQ to XML vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-104">Annotations in LINQ to XML enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="f7d7c-105">Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="f7d7c-106">Vous pouvez récupérer des annotations par type.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="f7d7c-107">Notez que les annotations ne font pas partie de l’Infoset XML. ils ne sont pas sérialisés ou désérialisés.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-107">Note that annotations aren't part of the XML infoset; they're not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="f7d7c-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f7d7c-108">Methods</span></span>

<span data-ttu-id="f7d7c-109">Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :</span><span class="sxs-lookup"><span data-stu-id="f7d7c-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="f7d7c-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="f7d7c-110">Method</span></span>|<span data-ttu-id="f7d7c-111">Description</span><span class="sxs-lookup"><span data-stu-id="f7d7c-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="f7d7c-112">Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="f7d7c-113">Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="f7d7c-114">Obtient une collection d’annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="f7d7c-115">Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f7d7c-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
