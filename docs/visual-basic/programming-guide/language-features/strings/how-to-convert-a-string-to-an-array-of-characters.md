---
title: 'Comment : convertir une chaîne en tableau de caractères'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352448"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="ce180-102">Comment : convertir une chaîne en tableau de caractères en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce180-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="ce180-103">Il est parfois utile d’avoir des données sur les caractères de votre chaîne et les positions de ces caractères dans votre chaîne, par exemple lorsque vous analysez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce180-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="ce180-104">Cet exemple montre comment obtenir un tableau de caractères dans une chaîne en appelant la méthode <xref:System.String.ToCharArray%2A> de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce180-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce180-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce180-105">Example</span></span>  
 <span data-ttu-id="ce180-106">Cet exemple montre comment fractionner une chaîne en tableau `Char` et comment fractionner une chaîne en un tableau `String` de ses caractères de texte Unicode.</span><span class="sxs-lookup"><span data-stu-id="ce180-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="ce180-107">Cette distinction est due au fait que les caractères de texte Unicode peuvent être composés d’au moins deux caractères `Char` (par exemple, une paire de substitution ou une séquence de caractères d’association).</span><span class="sxs-lookup"><span data-stu-id="ce180-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="ce180-108">Pour plus d’informations, consultez <xref:System.Globalization.TextElementEnumerator> et [la norme Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="ce180-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="ce180-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce180-109">Example</span></span>  
 <span data-ttu-id="ce180-110">Il est plus difficile de fractionner une chaîne en ses caractères de texte Unicode, mais cela est nécessaire si vous avez besoin d’informations sur la représentation visuelle d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce180-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="ce180-111">Cet exemple utilise la méthode <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> pour obtenir des informations sur les caractères de texte Unicode qui composent une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce180-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="ce180-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce180-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="ce180-113">Guide pratique : accéder aux caractères dans les chaînes</span><span class="sxs-lookup"><span data-stu-id="ce180-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="ce180-114">Conversion entre chaînes et d’autres types de données en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce180-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="ce180-115">Chaînes</span><span class="sxs-lookup"><span data-stu-id="ce180-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
