---
title: Valeurs de retour pour la fonction CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349988"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="f05dd-102">Valeurs de retour pour la fonction CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f05dd-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="f05dd-103">The following table describes the return values for `CStr` for different data types of `expression`.</span><span class="sxs-lookup"><span data-stu-id="f05dd-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="f05dd-104">If `expression` type is</span><span class="sxs-lookup"><span data-stu-id="f05dd-104">If `expression` type is</span></span>|<span data-ttu-id="f05dd-105">Retours `CStr`</span><span class="sxs-lookup"><span data-stu-id="f05dd-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="f05dd-106">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="f05dd-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="f05dd-107">A string containing "True" or "False".</span><span class="sxs-lookup"><span data-stu-id="f05dd-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="f05dd-108">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="f05dd-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="f05dd-109">A string containing a `Date` value (date and time) in the short date format of your system.</span><span class="sxs-lookup"><span data-stu-id="f05dd-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="f05dd-110">Types de données numériques</span><span class="sxs-lookup"><span data-stu-id="f05dd-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="f05dd-111">A string representing the number.</span><span class="sxs-lookup"><span data-stu-id="f05dd-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="f05dd-112">CStr and Date</span><span class="sxs-lookup"><span data-stu-id="f05dd-112">CStr and Date</span></span>  
 <span data-ttu-id="f05dd-113">The `Date` type always contains both date and time information.</span><span class="sxs-lookup"><span data-stu-id="f05dd-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="f05dd-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span><span class="sxs-lookup"><span data-stu-id="f05dd-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="f05dd-115">`CStr` does not include neutral values in the resulting string.</span><span class="sxs-lookup"><span data-stu-id="f05dd-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="f05dd-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span><span class="sxs-lookup"><span data-stu-id="f05dd-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="f05dd-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="f05dd-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f05dd-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span><span class="sxs-lookup"><span data-stu-id="f05dd-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="f05dd-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span><span class="sxs-lookup"><span data-stu-id="f05dd-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="f05dd-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span><span class="sxs-lookup"><span data-stu-id="f05dd-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05dd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f05dd-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="f05dd-122">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="f05dd-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f05dd-123">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="f05dd-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="f05dd-124">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="f05dd-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
