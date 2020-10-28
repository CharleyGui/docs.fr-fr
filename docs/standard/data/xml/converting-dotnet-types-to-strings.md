---
title: Conversion de types .NET en chaînes
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687625"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="a5e73-102">Convertir des types .NET en chaînes</span><span class="sxs-lookup"><span data-stu-id="a5e73-102">Convert .NET types to strings</span></span>

<span data-ttu-id="a5e73-103">Si vous souhaitez convertir un type .NET en chaîne, utilisez la méthode **ToString** .</span><span class="sxs-lookup"><span data-stu-id="a5e73-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="a5e73-104">La méthode **ToString** retourne une représentation sous forme de chaîne du type passé.</span><span class="sxs-lookup"><span data-stu-id="a5e73-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="a5e73-105">Le tableau suivant répertorie les types .NET qui retournent une chaîne dans un format mappé aux spécifications de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="a5e73-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="a5e73-106">Type .NET</span><span class="sxs-lookup"><span data-stu-id="a5e73-106">.NET type</span></span>|<span data-ttu-id="a5e73-107">Type de chaîne de retour</span><span class="sxs-lookup"><span data-stu-id="a5e73-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="a5e73-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="a5e73-108">Boolean</span></span>|<span data-ttu-id="a5e73-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="a5e73-109">"true", "false"</span></span>|  
|<span data-ttu-id="a5e73-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a5e73-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="a5e73-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="a5e73-111">"INF"</span></span>|  
|<span data-ttu-id="a5e73-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a5e73-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="a5e73-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a5e73-113">"-INF"</span></span>|  
|<span data-ttu-id="a5e73-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a5e73-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="a5e73-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="a5e73-115">"INF"</span></span>|  
|<span data-ttu-id="a5e73-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a5e73-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="a5e73-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a5e73-117">"-INF"</span></span>|  
|<span data-ttu-id="a5e73-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="a5e73-118">DateTime</span></span>|<span data-ttu-id="a5e73-119">Le format est yyyy-MM-ddTHH:mm:sszzzzzz et ses sous-ensembles.</span><span class="sxs-lookup"><span data-stu-id="a5e73-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="a5e73-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="a5e73-120">Timespan</span></span>|<span data-ttu-id="a5e73-121">Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="a5e73-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5e73-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5e73-122">See also</span></span>

- [<span data-ttu-id="a5e73-123">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="a5e73-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="a5e73-124">Conversion de chaînes en types de données .NET</span><span class="sxs-lookup"><span data-stu-id="a5e73-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
