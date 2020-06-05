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
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406382"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="5deda-102">Valeurs de retour pour la fonction CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5deda-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="5deda-103">Le tableau suivant décrit les valeurs de retour pour les `CStr` différents types de données de `expression` .</span><span class="sxs-lookup"><span data-stu-id="5deda-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="5deda-104">Si le `expression` type est</span><span class="sxs-lookup"><span data-stu-id="5deda-104">If `expression` type is</span></span>|<span data-ttu-id="5deda-105">Retours `CStr`</span><span class="sxs-lookup"><span data-stu-id="5deda-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="5deda-106">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="5deda-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="5deda-107">Chaîne contenant « true » ou « false ».</span><span class="sxs-lookup"><span data-stu-id="5deda-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="5deda-108">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="5deda-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="5deda-109">Chaîne contenant une `Date` valeur (date et heure) au format de date abrégée de votre système.</span><span class="sxs-lookup"><span data-stu-id="5deda-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="5deda-110">Types de données numériques</span><span class="sxs-lookup"><span data-stu-id="5deda-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="5deda-111">Chaîne représentant le nombre.</span><span class="sxs-lookup"><span data-stu-id="5deda-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="5deda-112">CStr et date</span><span class="sxs-lookup"><span data-stu-id="5deda-112">CStr and Date</span></span>  
 <span data-ttu-id="5deda-113">Le `Date` type contient toujours des informations de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="5deda-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="5deda-114">À des fins de conversion de type, Visual Basic considère que 1/1/0001 (1er janvier de l’année 1) comme étant une *valeur neutre* pour la date, et 00:00:00 (minuit) comme valeur neutre pour le moment.</span><span class="sxs-lookup"><span data-stu-id="5deda-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="5deda-115">`CStr`n’inclut pas de valeurs neutres dans la chaîne résultante.</span><span class="sxs-lookup"><span data-stu-id="5deda-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="5deda-116">Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en chaîne, le résultat est « 9:30:00 AM »; les informations de date sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="5deda-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="5deda-117">Toutefois, les informations de date sont toujours présentes dans la `Date` valeur d’origine et peuvent être récupérées avec des fonctions telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="5deda-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5deda-118">La `CStr` fonction effectue sa conversion en fonction des paramètres de culture actuels de l’application.</span><span class="sxs-lookup"><span data-stu-id="5deda-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="5deda-119">Pour obtenir la représentation sous forme de chaîne d’un nombre dans une culture particulière, utilisez la méthode du nombre `ToString(IFormatProvider)` .</span><span class="sxs-lookup"><span data-stu-id="5deda-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="5deda-120">Par exemple, utilisez <xref:System.Double.ToString%2A?displayProperty=nameWithType> lors de la conversion d’une valeur de type `Double` en `String` .</span><span class="sxs-lookup"><span data-stu-id="5deda-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5deda-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5deda-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="5deda-122">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5deda-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="5deda-123">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="5deda-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="5deda-124">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="5deda-124">Date Data Type</span></span>](../data-types/date-data-type.md)
