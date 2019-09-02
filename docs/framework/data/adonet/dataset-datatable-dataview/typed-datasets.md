---
title: Datasets typés
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203152"
---
# <a name="typed-datasets"></a><span data-ttu-id="edef8-102">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="edef8-102">Typed DataSets</span></span>
<span data-ttu-id="edef8-103">En plus d'un accès par liaison tardive aux valeurs via des variables faiblement typées, l'objet <xref:System.Data.DataSet> permet un accès aux données par l'intermédiaire d'une métaphore fortement typée.</span><span class="sxs-lookup"><span data-stu-id="edef8-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="edef8-104">Les tables et les colonnes qui font partie du **jeu de données** sont accessibles à l’aide de noms conviviaux et de variables fortement typées.</span><span class="sxs-lookup"><span data-stu-id="edef8-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="edef8-105">Un **DataSet** typé est une classe qui dérive d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="edef8-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="edef8-106">En tant que tel, il hérite de toutes les méthodes, événements et propriétés d’un **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="edef8-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="edef8-107">En outre, un **DataSet** typé fournit des méthodes, des événements et des propriétés fortement typés.</span><span class="sxs-lookup"><span data-stu-id="edef8-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="edef8-108">Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d'utiliser les méthodes associées à des collections.</span><span class="sxs-lookup"><span data-stu-id="edef8-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="edef8-109">Outre l’amélioration de la lisibilité du code, un **DataSet** typé permet également à l’éditeur de code Visual Studio .net de compléter automatiquement les lignes au fur et à mesure que vous tapez.</span><span class="sxs-lookup"><span data-stu-id="edef8-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="edef8-110">En outre, le **DataSet** fortement typé fournit l’accès aux valeurs en tant que type correct au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="edef8-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="edef8-111">Avec un **DataSet**fortement typé, les erreurs d’incompatibilité de types sont interceptées lorsque le code est compilé et non au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="edef8-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="edef8-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="edef8-112">In This Section</span></span>  
 [<span data-ttu-id="edef8-113">Génération de DataSets fortement typés</span><span class="sxs-lookup"><span data-stu-id="edef8-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="edef8-114">Décrit comment créer et utiliser un **DataSet**fortement typé.</span><span class="sxs-lookup"><span data-stu-id="edef8-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="edef8-115">Annotation de DataSets typés</span><span class="sxs-lookup"><span data-stu-id="edef8-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="edef8-116">Décrit comment annoter le schéma en langage XSD (XML Schema Definition) utilisé pour générer un **DataSet**fortement typé, afin de fournir des noms conviviaux aux éléments de **DataSet** sans altérer le schéma sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="edef8-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edef8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edef8-117">See also</span></span>

- [<span data-ttu-id="edef8-118">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="edef8-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="edef8-119">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="edef8-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
