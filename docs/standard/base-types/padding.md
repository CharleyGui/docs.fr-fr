---
title: Remplissage de chaînes dans .NET
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127624"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="d6448-102">Remplissage de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="d6448-102">Padding Strings in .NET</span></span>

<span data-ttu-id="d6448-103">Utilisez l’une des méthodes <xref:System.String> suivantes pour créer une chaîne qui se compose d’une chaîne d’origine remplie à l’aide de caractères de début ou de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6448-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="d6448-104">Le caractère de remplissage peut être un espace ou un caractère spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6448-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="d6448-105">La chaîne résultante apparaît alignée à droite ou à gauche.</span><span class="sxs-lookup"><span data-stu-id="d6448-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="d6448-106">Si la longueur de la chaîne d’origine est déjà égale ou supérieure à la longueur totale souhaitée, les méthodes de remplissage retournent la chaîne d’origine inchangée. Pour plus d’informations, consultez les sections **Retours** des deux surcharges des méthodes <xref:System.String.PadLeft%2A?displayProperty=nameWithType> et <xref:System.String.PadRight%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6448-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="d6448-107">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="d6448-107">Method name</span></span>|<span data-ttu-id="d6448-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="d6448-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="d6448-109">Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6448-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="d6448-110">Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6448-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="d6448-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="d6448-111">PadLeft</span></span>  
 <span data-ttu-id="d6448-112">La méthode <xref:System.String.PadLeft%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6448-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d6448-113">La méthode <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d6448-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d6448-114">L’exemple de code suivant utilise la méthode <xref:System.String.PadLeft%2A> pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="d6448-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d6448-115">L’exemple affiche « `--------Hello World!` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="d6448-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="d6448-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="d6448-116">PadRight</span></span>  
 <span data-ttu-id="d6448-117">La méthode <xref:System.String.PadRight%2A?displayProperty=nameWithType> crée une chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d6448-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d6448-118">La méthode <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> utilise l’espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d6448-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d6448-119">L’exemple de code suivant utilise la méthode <xref:System.String.PadRight%2A> pour créer une chaîne longue de vingt caractères.</span><span class="sxs-lookup"><span data-stu-id="d6448-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d6448-120">L’exemple affiche « `Hello World!--------` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="d6448-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d6448-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6448-121">See also</span></span>

- [<span data-ttu-id="d6448-122">Opérations de base des cordes</span><span class="sxs-lookup"><span data-stu-id="d6448-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
