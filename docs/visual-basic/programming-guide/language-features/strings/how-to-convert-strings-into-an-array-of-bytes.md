---
title: 'Guide pratique : convertir des chaînes en tableau d’octets'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 3ee1d5e1e31054f23f4510c7a112d8e3473bcdd7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410604"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="2559f-102">Comment : convertir des chaînes en tableau d'octets en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2559f-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="2559f-103">Cette rubrique montre comment convertir une chaîne en un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="2559f-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2559f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2559f-104">Example</span></span>  
 <span data-ttu-id="2559f-105">Cet exemple utilise la <xref:System.Text.Encoding.GetBytes%2A> méthode de la <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> classe Encoding pour convertir une chaîne en un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="2559f-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 <span data-ttu-id="2559f-106">Vous pouvez choisir parmi plusieurs options d’encodage pour convertir une chaîne en un tableau d’octets :</span><span class="sxs-lookup"><span data-stu-id="2559f-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
- <span data-ttu-id="2559f-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Obtient un encodage pour le jeu de caractères ASCII (7 bits).</span><span class="sxs-lookup"><span data-stu-id="2559f-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="2559f-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Obtient un encodage pour le format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).</span><span class="sxs-lookup"><span data-stu-id="2559f-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="2559f-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Obtient un encodage pour la page de codes ANSI actuelle du système.</span><span class="sxs-lookup"><span data-stu-id="2559f-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="2559f-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Obtient un encodage pour le format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="2559f-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="2559f-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Obtient un encodage pour le format UTF-32 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).</span><span class="sxs-lookup"><span data-stu-id="2559f-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="2559f-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Obtient un encodage pour le format UTF-7.</span><span class="sxs-lookup"><span data-stu-id="2559f-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="2559f-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Obtient un encodage pour le format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2559f-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2559f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2559f-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="2559f-115">Comment : convertir un tableau d'octets en chaîne en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2559f-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](how-to-convert-an-array-of-bytes-into-a-string.md)
