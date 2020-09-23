---
title: Types de données caractères
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 5fde5eff40d83bdd7d90cd611bd6749106db6e16
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077174"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="5ef3d-102">Types de données caractères (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ef3d-102">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="5ef3d-103">Visual Basic fournit des *types de données caractères* pour gérer les caractères imprimables et affichables.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="5ef3d-104">Bien qu’ils traitent tous deux des caractères Unicode, contient `Char` un caractère unique, tandis que `String` contient un nombre indéfini de caractères.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="5ef3d-105">Pour obtenir une table qui affiche une comparaison côte à côte des types de données Visual Basic, consultez [types de données](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ef3d-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="5ef3d-106">Char, type</span><span class="sxs-lookup"><span data-stu-id="5ef3d-106">Char Type</span></span>  

 <span data-ttu-id="5ef3d-107">Le `Char` type de données est un caractère Unicode codé sur deux octets (16 bits).</span><span class="sxs-lookup"><span data-stu-id="5ef3d-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="5ef3d-108">Si une variable stocke toujours un caractère exactement, déclarez-la comme `Char` .</span><span class="sxs-lookup"><span data-stu-id="5ef3d-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="5ef3d-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5ef3d-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="5ef3d-110">Chaque valeur possible dans une `Char` `String` variable ou est un *point de code*, ou code de caractère, dans le jeu de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="5ef3d-111">Les caractères Unicode incluent le jeu de caractères ASCII de base, les autres lettres de l’alphabet, les accents, les symboles monétaires, les fractions, les signes diacritiques et les symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ef3d-112">Le jeu de caractères Unicode réserve les points de code D800 à DFFF (55296 à 55551 décimal) pour les *paires de substitution*, qui requièrent des valeurs de 2 16 bits pour représenter un point de code unique.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="5ef3d-113">Une `Char` variable ne peut pas contenir une paire de substitution et un `String` utilise deux positions pour contenir une telle paire.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="5ef3d-114">Pour plus d’informations, consultez [type de données char](../../../language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="5ef3d-114">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="5ef3d-115">Type de chaîne</span><span class="sxs-lookup"><span data-stu-id="5ef3d-115">String Type</span></span>  

 <span data-ttu-id="5ef3d-116">Le `String` type de données est une séquence de zéro, un ou plusieurs caractères Unicode (16 bits) de 2 octets.</span><span class="sxs-lookup"><span data-stu-id="5ef3d-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="5ef3d-117">Si une variable peut contenir un nombre indéfini de caractères, déclarez-la comme `String` .</span><span class="sxs-lookup"><span data-stu-id="5ef3d-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="5ef3d-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5ef3d-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="5ef3d-119">Pour plus d’informations, consultez [type de données String](../../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="5ef3d-119">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef3d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ef3d-120">See also</span></span>

- [<span data-ttu-id="5ef3d-121">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="5ef3d-121">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="5ef3d-122">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="5ef3d-122">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="5ef3d-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ef3d-123">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="5ef3d-124">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="5ef3d-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="5ef3d-125">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ef3d-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5ef3d-126">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="5ef3d-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="5ef3d-127">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="5ef3d-127">Type Characters</span></span>](type-characters.md)
