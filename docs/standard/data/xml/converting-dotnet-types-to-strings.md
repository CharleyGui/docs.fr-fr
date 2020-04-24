---
title: Conversion de types .NET Framework en chaînes
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711075"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="38cec-102">Conversion de types .NET Framework en chaînes</span><span class="sxs-lookup"><span data-stu-id="38cec-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="38cec-103">Si vous voulez convertir un type .NET Framework en chaîne, utilisez la méthode **ToString**.</span><span class="sxs-lookup"><span data-stu-id="38cec-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="38cec-104">La méthode **ToString** retourne une représentation sous forme de chaîne du type passé.</span><span class="sxs-lookup"><span data-stu-id="38cec-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="38cec-105">Le tableau suivant répertorie les types .NET Framework qui retournent une chaîne dans un format qui mappe aux spécifications de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="38cec-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="38cec-106">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38cec-106">.NET Framework type</span></span>|<span data-ttu-id="38cec-107">Type de chaîne de retour</span><span class="sxs-lookup"><span data-stu-id="38cec-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="38cec-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="38cec-108">Boolean</span></span>|<span data-ttu-id="38cec-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="38cec-109">"true", "false"</span></span>|  
|<span data-ttu-id="38cec-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="38cec-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="38cec-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="38cec-111">"INF"</span></span>|  
|<span data-ttu-id="38cec-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="38cec-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="38cec-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="38cec-113">"-INF"</span></span>|  
|<span data-ttu-id="38cec-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="38cec-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="38cec-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="38cec-115">"INF"</span></span>|  
|<span data-ttu-id="38cec-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="38cec-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="38cec-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="38cec-117">"-INF"</span></span>|  
|<span data-ttu-id="38cec-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="38cec-118">DateTime</span></span>|<span data-ttu-id="38cec-119">Le format est yyyy-MM-ddTHH:mm:sszzzzzz et ses sous-ensembles.</span><span class="sxs-lookup"><span data-stu-id="38cec-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="38cec-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="38cec-120">Timespan</span></span>|<span data-ttu-id="38cec-121">Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="38cec-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38cec-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38cec-122">See also</span></span>

- [<span data-ttu-id="38cec-123">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="38cec-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="38cec-124">Conversion de chaînes en types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38cec-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
