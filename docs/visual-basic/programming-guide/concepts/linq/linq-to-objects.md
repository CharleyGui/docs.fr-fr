---
title: LINQ to Objects
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: cb277a255151bf7db9d0fb0a50605ee07ba1423f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075289"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="e6368-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-102">LINQ to Objects (Visual Basic)</span></span>

<span data-ttu-id="e6368-103">« LINQ to Objects » fait référence à l’utilisation directe de requêtes LINQ avec n’importe quelle collection <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, sans utiliser de fournisseur LINQ ou d’API intermédiaire comme [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e6368-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="e6368-104">Vous pouvez utiliser LINQ pour interroger des collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="e6368-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e6368-105">La collection peut être définie par l’utilisateur ou retournée par une API du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6368-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="e6368-106">Fondamentalement, LINQ to Objects représente une nouvelle approche des collections.</span><span class="sxs-lookup"><span data-stu-id="e6368-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="e6368-107">Auparavant, vous deviez écrire des boucles `For Each` complexes pour spécifier comment récupérer les données d'une collection.</span><span class="sxs-lookup"><span data-stu-id="e6368-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="e6368-108">Avec l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous voulez récupérer.</span><span class="sxs-lookup"><span data-stu-id="e6368-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="e6368-109">De plus, les requêtes LINQ offrent trois avantages principaux par rapport aux boucles `For Each` classiques :</span><span class="sxs-lookup"><span data-stu-id="e6368-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="e6368-110">Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.</span><span class="sxs-lookup"><span data-stu-id="e6368-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="e6368-111">Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.</span><span class="sxs-lookup"><span data-stu-id="e6368-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="e6368-112">Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.</span><span class="sxs-lookup"><span data-stu-id="e6368-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="e6368-113">En général, plus l’opération que vous voulez effectuer sur les données est complexe, plus vous avez intérêt à utiliser LINQ à la place des techniques d’itération classiques.</span><span class="sxs-lookup"><span data-stu-id="e6368-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="e6368-114">Cette section a pour objectif de montrer l’approche basée sur LINQ avec quelques exemples sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="e6368-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="e6368-115">Elle ne se veut pas exhaustive.</span><span class="sxs-lookup"><span data-stu-id="e6368-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6368-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e6368-116">In This Section</span></span>  

 [<span data-ttu-id="e6368-117">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="e6368-118">Explique comment LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e6368-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="e6368-119">Inclut également des liens vers les rubriques qui présentent ces principes.</span><span class="sxs-lookup"><span data-stu-id="e6368-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="e6368-120">LINQ et réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-120">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="e6368-121">Contient un lien vers un exemple qui montre comment LINQ utilise la réflexion.</span><span class="sxs-lookup"><span data-stu-id="e6368-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="e6368-122">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-122">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="e6368-123">Explique comment LINQ peut être utilisé pour interagir avec les systèmes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="e6368-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="e6368-124">Inclut également des liens vers les rubriques qui présentent ces concepts.</span><span class="sxs-lookup"><span data-stu-id="e6368-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="e6368-125">Comment : interroger un ArrayList avec LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="e6368-126">Montre comment interroger une ArrayList en C#.</span><span class="sxs-lookup"><span data-stu-id="e6368-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="e6368-127">Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="e6368-128">Explique comment étendre l'ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d'extension à l'interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e6368-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="e6368-129">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6368-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="e6368-130">Fournit des liens vers des rubriques qui présentent LINQ, ainsi que des exemples de code effectuant des requêtes.</span><span class="sxs-lookup"><span data-stu-id="e6368-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
