---
title: Annotations LINQ to XML
description: Apprenez à utiliser des annotations dans LINQ to XML pour associer tout objet arbitraire de tout type arbitraire à n’importe quel composant XML dans une arborescence XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165570"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="ae83e-103">Annotations LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ae83e-103">LINQ to XML Annotations</span></span>

<span data-ttu-id="ae83e-104">Les annotations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="ae83e-104">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="ae83e-105">Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83e-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="ae83e-106">Vous pouvez récupérer des annotations par type.</span><span class="sxs-lookup"><span data-stu-id="ae83e-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="ae83e-107">Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="ae83e-107">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="ae83e-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ae83e-108">Methods</span></span>

<span data-ttu-id="ae83e-109">Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :</span><span class="sxs-lookup"><span data-stu-id="ae83e-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="ae83e-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="ae83e-110">Method</span></span>|<span data-ttu-id="ae83e-111">Description</span><span class="sxs-lookup"><span data-stu-id="ae83e-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="ae83e-112">Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae83e-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="ae83e-113">Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae83e-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="ae83e-114">Obtient une collection d’annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae83e-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="ae83e-115">Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="ae83e-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
