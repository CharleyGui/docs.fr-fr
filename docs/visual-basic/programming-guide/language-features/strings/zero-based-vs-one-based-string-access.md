---
title: Accès à une chaîne de base zéro et à un
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072286"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5377f-102">Accès à une chaîne de base zéro et accès à une chaîne de base un en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5377f-102">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="5377f-103">Cette rubrique compare comment Visual Basic et les .NET Framework fournissent l’accès aux caractères d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5377f-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="5377f-104">Le .NET Framework fournit toujours un accès de base zéro aux caractères d’une chaîne, tandis que Visual Basic fournit un accès de base zéro et un accès de base zéro, selon la fonction.</span><span class="sxs-lookup"><span data-stu-id="5377f-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5377f-105">Basé sur un</span><span class="sxs-lookup"><span data-stu-id="5377f-105">One-Based</span></span>  

 <span data-ttu-id="5377f-106">Pour obtenir un exemple d’une fonction de Visual Basic basée sur un, considérez la `Mid` fonction.</span><span class="sxs-lookup"><span data-stu-id="5377f-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="5377f-107">Il accepte un argument qui indique la position de caractère à laquelle la sous-chaîne commencera, en commençant par la position 1.</span><span class="sxs-lookup"><span data-stu-id="5377f-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5377f-108">La <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode .NET Framework prend un index du caractère dans la chaîne à laquelle la sous-chaîne doit commencer, en commençant par la position 0.</span><span class="sxs-lookup"><span data-stu-id="5377f-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5377f-109">Ainsi, si vous avez une chaîne « ABCDe », les caractères individuels sont numérotés 1, 2, 3, 4, 5 pour une utilisation avec la `Mid` fonction, mais 0, 1, 2, 3, 4 pour une utilisation avec la <xref:System.String.Substring%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="5377f-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5377f-110">De base zéro</span><span class="sxs-lookup"><span data-stu-id="5377f-110">Zero-Based</span></span>  

 <span data-ttu-id="5377f-111">Pour obtenir un exemple de fonction Visual Basic de base zéro, considérez la `Split` fonction.</span><span class="sxs-lookup"><span data-stu-id="5377f-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="5377f-112">Il fractionne une chaîne et retourne un tableau contenant les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="5377f-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5377f-113">La <xref:System.String.Split%2A?displayProperty=nameWithType> méthode .NET Framework fractionne également une chaîne et retourne un tableau contenant les sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="5377f-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5377f-114">Étant donné que la `Split` fonction et la <xref:System.String.Split%2A> méthode retournent des tableaux .NET Framework, ils doivent être de base zéro.</span><span class="sxs-lookup"><span data-stu-id="5377f-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5377f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5377f-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="5377f-116">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5377f-116">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
