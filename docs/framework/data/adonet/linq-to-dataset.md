---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783788"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="bfdd4-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bfdd4-102">LINQ to DataSet</span></span>
<span data-ttu-id="bfdd4-103">LINQ to DataSet facilite et accélère l’interrogation de données mises en cache dans un <xref:System.Data.DataSet> objet.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="bfdd4-104">Plus précisément, LINQ to DataSet simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes à partir du langage de programmation lui-même, au lieu d’utiliser un langage de requête séparé.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="bfdd4-105">Ceci est particulièrement utile pour les développeurs Visual Studio, qui peuvent désormais tirer parti de la vérification de la syntaxe au moment de la compilation, du typage statique et de la prise en charge IntelliSense fournis par Visual Studio dans leurs requêtes.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="bfdd4-106">LINQ to DataSet peut également être utilisé pour interroger des données qui ont été consolidées à partir d’une ou de plusieurs sources de données.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="bfdd4-107">Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="bfdd4-108">En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="bfdd4-109">La fonctionnalité de LINQ to DataSet est exposée principalement à travers les méthodes <xref:System.Data.DataRowExtensions> d' <xref:System.Data.DataTableExtensions> extension dans les classes et.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="bfdd4-110">LINQ to DataSet repose sur et utilise l’architecture ADO.NET existante et n’est pas destinée à remplacer ADO.NET dans le code de l’application.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="bfdd4-111">Le code ADO.NET existant continuera à fonctionner dans une application LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="bfdd4-112">La relation entre LINQ to DataSet et ADO.NET et le magasin de données est illustrée dans le diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="bfdd4-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagramme montrant que LINQ to DataSet est basé sur le fournisseur ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="bfdd4-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bfdd4-114">In This Section</span></span>  
 [<span data-ttu-id="bfdd4-115">Prise en main</span><span class="sxs-lookup"><span data-stu-id="bfdd4-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="bfdd4-116">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="bfdd4-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="bfdd4-117">Référence</span><span class="sxs-lookup"><span data-stu-id="bfdd4-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="bfdd4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfdd4-118">See also</span></span>

- [<span data-ttu-id="bfdd4-119">LINQ (Language-Integrated Query) - C#</span><span class="sxs-lookup"><span data-stu-id="bfdd4-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="bfdd4-120">LINQ (Language-Integrated Query) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfdd4-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="bfdd4-121">LINQ et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bfdd4-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="bfdd4-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bfdd4-122">ADO.NET</span></span>](index.md)
