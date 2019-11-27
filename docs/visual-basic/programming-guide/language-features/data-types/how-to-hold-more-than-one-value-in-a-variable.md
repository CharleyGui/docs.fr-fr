---
title: 'Comment : stocker plusieurs valeurs dans une variable'
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
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350021"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="2de86-102">Comment : stocker plusieurs valeurs dans une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2de86-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="2de86-103">Une variable contient plusieurs valeurs si vous la déclarez comme étant d’un *type de données composite*.</span><span class="sxs-lookup"><span data-stu-id="2de86-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="2de86-104">Les [types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluent des structures, des tableaux et des classes.</span><span class="sxs-lookup"><span data-stu-id="2de86-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="2de86-105">Une variable d’un type de données composite peut contenir une combinaison de types de données élémentaires et d’autres types composites.</span><span class="sxs-lookup"><span data-stu-id="2de86-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="2de86-106">Les structures et les classes peuvent contenir du code ainsi que des données.</span><span class="sxs-lookup"><span data-stu-id="2de86-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="2de86-107">Pour stocker plusieurs valeurs dans une variable</span><span class="sxs-lookup"><span data-stu-id="2de86-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="2de86-108">Déterminez le type de données composite que vous souhaitez utiliser pour votre variable.</span><span class="sxs-lookup"><span data-stu-id="2de86-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="2de86-109">Si le type de données composite n’est pas déjà défini, définissez-le afin que votre variable puisse l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="2de86-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="2de86-110">Définissez une structure avec une [instruction structure](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2de86-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="2de86-111">Définissez un tableau avec une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2de86-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="2de86-112">Définissez une classe avec une [instruction de classe](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2de86-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="2de86-113">Déclarez votre variable avec une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="2de86-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="2de86-114">Suivez le nom de la variable avec une clause `As`.</span><span class="sxs-lookup"><span data-stu-id="2de86-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="2de86-115">Suivez le mot clé `As` avec le nom du type de données composite approprié.</span><span class="sxs-lookup"><span data-stu-id="2de86-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="2de86-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2de86-116">See also</span></span>

- [<span data-ttu-id="2de86-117">Types de données</span><span class="sxs-lookup"><span data-stu-id="2de86-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="2de86-118">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="2de86-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="2de86-119">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="2de86-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="2de86-120">Structures</span><span class="sxs-lookup"><span data-stu-id="2de86-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2de86-121">Tableaux</span><span class="sxs-lookup"><span data-stu-id="2de86-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="2de86-122">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="2de86-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="2de86-123">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="2de86-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
