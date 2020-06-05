---
title: 'Procédure : Stocker plusieurs valeurs dans une variable'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393894"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="41eea-102">Comment : stocker plusieurs valeurs dans une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41eea-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="41eea-103">Une variable contient plusieurs valeurs si vous la déclarez comme étant d’un *type de données composite*.</span><span class="sxs-lookup"><span data-stu-id="41eea-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="41eea-104">Les [types de données composites](composite-data-types.md) incluent des structures, des tableaux et des classes.</span><span class="sxs-lookup"><span data-stu-id="41eea-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="41eea-105">Une variable d’un type de données composite peut contenir une combinaison de types de données élémentaires et d’autres types composites.</span><span class="sxs-lookup"><span data-stu-id="41eea-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="41eea-106">Les structures et les classes peuvent contenir du code ainsi que des données.</span><span class="sxs-lookup"><span data-stu-id="41eea-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="41eea-107">Pour stocker plusieurs valeurs dans une variable</span><span class="sxs-lookup"><span data-stu-id="41eea-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="41eea-108">Déterminez le type de données composite que vous souhaitez utiliser pour votre variable.</span><span class="sxs-lookup"><span data-stu-id="41eea-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="41eea-109">Si le type de données composite n’est pas déjà défini, définissez-le afin que votre variable puisse l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="41eea-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="41eea-110">Définissez une structure avec une [instruction structure](../../../language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="41eea-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="41eea-111">Définissez un tableau avec une [instruction Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="41eea-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="41eea-112">Définissez une classe avec une [instruction de classe](../../../language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="41eea-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="41eea-113">Déclarez votre variable avec une `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="41eea-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="41eea-114">Suivez le nom de la variable avec une `As` clause.</span><span class="sxs-lookup"><span data-stu-id="41eea-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="41eea-115">Suivez le `As` mot clé avec le nom du type de données composite approprié.</span><span class="sxs-lookup"><span data-stu-id="41eea-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="41eea-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41eea-116">See also</span></span>

- [<span data-ttu-id="41eea-117">Types de données</span><span class="sxs-lookup"><span data-stu-id="41eea-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="41eea-118">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="41eea-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="41eea-119">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="41eea-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="41eea-120">Structures</span><span class="sxs-lookup"><span data-stu-id="41eea-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="41eea-121">Tableaux</span><span class="sxs-lookup"><span data-stu-id="41eea-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="41eea-122">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="41eea-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="41eea-123">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="41eea-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
