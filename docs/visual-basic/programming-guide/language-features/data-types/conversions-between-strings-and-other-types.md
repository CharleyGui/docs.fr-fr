---
title: Conversions entre des chaînes et d’autres types
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077148"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="e243c-102">Conversion entre des chaînes et d'autres types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e243c-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="e243c-103">Vous pouvez convertir une valeur numérique, `Boolean` ou de date/heure en `String` .</span><span class="sxs-lookup"><span data-stu-id="e243c-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="e243c-104">Vous pouvez également convertir dans le sens inverse (à partir d’une valeur de chaîne en numeric, `Boolean` ou), à `Date` condition que le contenu de la chaîne puisse être interprété comme une valeur valide du type de données de destination.</span><span class="sxs-lookup"><span data-stu-id="e243c-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="e243c-105">Si ce n’est pas le cas, une erreur d’exécution se produit.</span><span class="sxs-lookup"><span data-stu-id="e243c-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="e243c-106">Les conversions pour toutes ces assignations, dans les deux sens, sont des conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="e243c-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="e243c-107">Vous devez utiliser les mots clés de conversion de type ( `CBool` , `CByte` , `CDate` , `CDbl` , `CDec` , `CInt` , `CLng` , `CSByte` , `CShort` , `CSng` , `CStr` , `CUInt` , `CULng` , `CUShort` et `CType` ).</span><span class="sxs-lookup"><span data-stu-id="e243c-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="e243c-108">Les <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A> fonctions et vous offrent un contrôle supplémentaire sur les conversions entre les chaînes et les nombres.</span><span class="sxs-lookup"><span data-stu-id="e243c-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="e243c-109">Si vous avez défini une classe ou une structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="e243c-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="e243c-110">Pour plus d'informations, consultez [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e243c-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="e243c-111">Conversion de nombres en chaînes</span><span class="sxs-lookup"><span data-stu-id="e243c-111">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="e243c-112">Vous pouvez utiliser la `Format` fonction pour convertir un nombre en chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés, mais également mettre en forme les symboles tels que les symboles monétaires (tels que `$` ), les séparateurs de milliers ou les *symboles de groupement de chiffres* (tels que) `,` et un séparateur décimal (tel que `.` ).</span><span class="sxs-lookup"><span data-stu-id="e243c-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="e243c-113">`Format` utilise automatiquement les symboles appropriés en fonction des paramètres **régionaux** spécifiés dans le **panneau**de configuration Windows.</span><span class="sxs-lookup"><span data-stu-id="e243c-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="e243c-114">Notez que l’opérateur de concaténation ( `&` ) peut convertir un nombre en chaîne implicitement, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e243c-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="e243c-115">Conversion de chaînes en nombres</span><span class="sxs-lookup"><span data-stu-id="e243c-115">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="e243c-116">Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en nombre.</span><span class="sxs-lookup"><span data-stu-id="e243c-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="e243c-117">`Val` lit la chaîne jusqu’à ce qu’elle rencontre un caractère autre qu’un chiffre, un espace, une tabulation, un saut de ligne ou un point.</span><span class="sxs-lookup"><span data-stu-id="e243c-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="e243c-118">Les séquences « &O » et « &H » modifient la base du système de nombres et terminent l’analyse.</span><span class="sxs-lookup"><span data-stu-id="e243c-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="e243c-119">Jusqu’à ce qu’il arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="e243c-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="e243c-120">Par exemple, l’instruction suivante retourne la valeur `141.825` .</span><span class="sxs-lookup"><span data-stu-id="e243c-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="e243c-121">Lorsque Visual Basic convertit une chaîne en une valeur numérique, elle utilise les paramètres **régionaux** spécifiés dans le **panneau de configuration** Windows pour interpréter le séparateur des milliers, le séparateur décimal et le symbole monétaire.</span><span class="sxs-lookup"><span data-stu-id="e243c-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="e243c-122">Cela signifie qu’une conversion peut échouer sous un seul paramètre, mais pas dans un autre.</span><span class="sxs-lookup"><span data-stu-id="e243c-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="e243c-123">Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans les paramètres régionaux français.</span><span class="sxs-lookup"><span data-stu-id="e243c-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e243c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e243c-124">See also</span></span>

- [<span data-ttu-id="e243c-125">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e243c-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="e243c-126">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="e243c-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e243c-127">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="e243c-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e243c-128">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e243c-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="e243c-129">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="e243c-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="e243c-130">Data types</span><span class="sxs-lookup"><span data-stu-id="e243c-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="e243c-131">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="e243c-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e243c-132">Développer des applications mondialisées et traduites</span><span class="sxs-lookup"><span data-stu-id="e243c-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
