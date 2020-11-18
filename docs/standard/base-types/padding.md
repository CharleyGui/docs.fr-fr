---
title: Remplissage de chaînes dans .NET
description: Découvrez comment remplir des chaînes dans .NET. Utilisez les méthodes String. PadLeft et String. PadRight pour ajouter des caractères de début ou de fin pour atteindre une longueur totale spécifiée.
ms.date: 03/15/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 9931db1e76e3737ab3803400928169b30c3ecbda
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822943"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="d3991-104">Remplissage de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="d3991-104">Padding Strings in .NET</span></span>

<span data-ttu-id="d3991-105">Utilisez l’une des méthodes <xref:System.String> suivantes pour créer une chaîne qui se compose d’une chaîne d’origine remplie à l’aide de caractères de début ou de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3991-105">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="d3991-106">Le caractère de remplissage peut être un espace ou un caractère spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3991-106">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="d3991-107">La chaîne résultante apparaît alignée à droite ou à gauche.</span><span class="sxs-lookup"><span data-stu-id="d3991-107">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="d3991-108">Si la longueur de la chaîne d’origine est déjà égale ou supérieure à la longueur totale souhaitée, les méthodes de remplissage retournent la chaîne d’origine inchangée. Pour plus d’informations, consultez les sections **Retours** des deux surcharges des méthodes <xref:System.String.PadLeft%2A?displayProperty=nameWithType> et <xref:System.String.PadRight%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d3991-108">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="d3991-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="d3991-109">Method name</span></span>|<span data-ttu-id="d3991-110">Utilisation</span><span class="sxs-lookup"><span data-stu-id="d3991-110">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="d3991-111">Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3991-111">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="d3991-112">Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3991-112">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="d3991-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="d3991-113">PadLeft</span></span>  
 <span data-ttu-id="d3991-114">La méthode <xref:System.String.PadLeft%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3991-114">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d3991-115">La méthode <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d3991-115">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d3991-116">L’exemple de code suivant utilise la méthode <xref:System.String.PadLeft%2A> pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="d3991-116">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d3991-117">L’exemple affiche « `--------Hello World!` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="d3991-117">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="d3991-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="d3991-118">PadRight</span></span>  
 <span data-ttu-id="d3991-119">La méthode <xref:System.String.PadRight%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3991-119">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d3991-120">La méthode <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d3991-120">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d3991-121">L’exemple de code suivant utilise la méthode <xref:System.String.PadRight%2A> pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="d3991-121">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d3991-122">L’exemple affiche « `Hello World!--------` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="d3991-122">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d3991-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3991-123">See also</span></span>

- [<span data-ttu-id="d3991-124">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="d3991-124">Basic String Operations</span></span>](basic-string-operations.md)
