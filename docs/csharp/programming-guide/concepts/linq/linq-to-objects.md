---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344783"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="cf44d-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="cf44d-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="cf44d-103">« LINQ to Objects » fait référence à l’utilisation directe de requêtes LINQ avec n’importe quelle collection <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, sans utiliser de fournisseur LINQ ou d’API intermédiaire comme [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cf44d-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="cf44d-104">Vous pouvez utiliser LINQ pour interroger des collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="cf44d-105">La collection peut être définie par l’utilisateur ou retournée par une API du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf44d-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="cf44d-106">Fondamentalement, LINQ to Objects représente une nouvelle approche des collections.</span><span class="sxs-lookup"><span data-stu-id="cf44d-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="cf44d-107">Auparavant, vous deviez écrire des boucles `foreach` complexes pour spécifier comment récupérer les données d'une collection.</span><span class="sxs-lookup"><span data-stu-id="cf44d-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="cf44d-108">Avec l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous voulez récupérer.</span><span class="sxs-lookup"><span data-stu-id="cf44d-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="cf44d-109">De plus, les requêtes LINQ offrent trois avantages principaux par rapport aux boucles `foreach` classiques :</span><span class="sxs-lookup"><span data-stu-id="cf44d-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="cf44d-110">Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="cf44d-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="cf44d-111">Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.</span><span class="sxs-lookup"><span data-stu-id="cf44d-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="cf44d-112">Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.</span><span class="sxs-lookup"><span data-stu-id="cf44d-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="cf44d-113">En général, plus l’opération que vous voulez effectuer sur les données est complexe, plus vous avez intérêt à utiliser LINQ à la place des techniques d’itération classiques.</span><span class="sxs-lookup"><span data-stu-id="cf44d-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="cf44d-114">Cette section a pour objectif de montrer l’approche basée sur LINQ avec quelques exemples sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="cf44d-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="cf44d-115">Elle ne se veut pas exhaustive.</span><span class="sxs-lookup"><span data-stu-id="cf44d-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf44d-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cf44d-116">In This Section</span></span>  
 [<span data-ttu-id="cf44d-117">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="cf44d-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="cf44d-118">Explique comment LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes.</span><span class="sxs-lookup"><span data-stu-id="cf44d-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="cf44d-119">Inclut également des liens vers les rubriques qui présentent ces principes.</span><span class="sxs-lookup"><span data-stu-id="cf44d-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="cf44d-120">LINQ et la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="cf44d-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="cf44d-121">Contient un lien vers un exemple qui montre comment LINQ utilise la réflexion.</span><span class="sxs-lookup"><span data-stu-id="cf44d-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="cf44d-122">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="cf44d-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="cf44d-123">Explique comment LINQ peut être utilisé pour interagir avec les systèmes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="cf44d-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="cf44d-124">Inclut également des liens vers les rubriques qui présentent ces concepts.</span><span class="sxs-lookup"><span data-stu-id="cf44d-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="cf44d-125">Comment interroger un ArrayList avec LINQ (C)</span><span class="sxs-lookup"><span data-stu-id="cf44d-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="cf44d-126">Montre comment interroger une ArrayList en C#.</span><span class="sxs-lookup"><span data-stu-id="cf44d-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="cf44d-127">Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C)</span><span class="sxs-lookup"><span data-stu-id="cf44d-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="cf44d-128">Explique comment étendre l'ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d'extension à l'interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cf44d-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="cf44d-129">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="cf44d-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="cf44d-130">Fournit des liens vers des rubriques qui présentent LINQ, ainsi que des exemples de code effectuant des requêtes.</span><span class="sxs-lookup"><span data-stu-id="cf44d-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
