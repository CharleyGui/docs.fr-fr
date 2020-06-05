---
title: Date (type de données)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 46c25e14db56d4cc3c6d59ec7649b37c35676e2e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387424"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="9d796-102">Type de données date (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d796-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="9d796-103">Contient des valeurs sous la forme IEEE 64 bits (8 octets) qui représentent des dates comprises entre le 1er janvier de l'année 0001 et le 31 décembre de l'année 9999 et des heures comprises entre de 0:00:00 (minuit) et 23:59:59,9999999.</span><span class="sxs-lookup"><span data-stu-id="9d796-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="9d796-104">Chaque incrément représente 100 nanosecondes de durée calendaire depuis le début du 1er janvier de l’année 1 du calendrier grégorien.</span><span class="sxs-lookup"><span data-stu-id="9d796-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="9d796-105">La valeur maximale représente 100 nanosecondes avant le début du 1er janvier de l'année 10 000.</span><span class="sxs-lookup"><span data-stu-id="9d796-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d796-106">Notes</span><span class="sxs-lookup"><span data-stu-id="9d796-106">Remarks</span></span>

<span data-ttu-id="9d796-107">Utilisez le type de données `Date` comme conteneur de valeurs de date, de valeurs d'heure ou de valeurs de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="9d796-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="9d796-108">La valeur par défaut de `Date` est 0:00:00 (minuit) le 1er janvier 0001.</span><span class="sxs-lookup"><span data-stu-id="9d796-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="9d796-109">Vous pouvez obtenir les date et heure actuelles à partir de la classe <xref:Microsoft.VisualBasic.DateAndTime>.</span><span class="sxs-lookup"><span data-stu-id="9d796-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="9d796-110">Exigences relatives au format</span><span class="sxs-lookup"><span data-stu-id="9d796-110">Format Requirements</span></span>

<span data-ttu-id="9d796-111">Vous devez placer un littéral `Date` entre des signes dièse (`# #`).</span><span class="sxs-lookup"><span data-stu-id="9d796-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="9d796-112">Vous devez spécifier la valeur de date au format M/j/aaaa, par exemple `#5/31/1993#`, ou aaaa-MM-jj, par exemple `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="9d796-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="9d796-113">Vous pouvez utiliser des barres obliques quand vous spécifiez l'année en premier.</span><span class="sxs-lookup"><span data-stu-id="9d796-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="9d796-114">Cette exigence est indépendante de vos paramètres régionaux et des paramètres de format de date et d’heure de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9d796-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="9d796-115">Cette restriction tient au fait que la signification de votre code ne doit jamais changer en fonction des paramètres régionaux dans lesquels votre application s'exécute.</span><span class="sxs-lookup"><span data-stu-id="9d796-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="9d796-116">Supposez que vous codez en dur un littéral `Date` égal à `#3/4/1998#` et qu'il doit correspondre au 4 mars 1998.</span><span class="sxs-lookup"><span data-stu-id="9d796-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="9d796-117">Dans des paramètres régionaux qui utilisent le format mm/jj/aaaa, la date 3/4/1998 est compilée comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="9d796-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="9d796-118">Mais supposons que vous déployiez votre application dans de nombreux pays ou régions.</span><span class="sxs-lookup"><span data-stu-id="9d796-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="9d796-119">Dans des paramètres régionaux qui utilisent le format jj/mm/aaaa, votre littéral codé en dur sera compilé en tant que 3 avril 1998.</span><span class="sxs-lookup"><span data-stu-id="9d796-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="9d796-120">Dans des paramètres régionaux qui utilisent le format aaaa/mm/jj, le littéral sera non valide (avril 1998, 0003) et provoquera une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9d796-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="9d796-121">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="9d796-121">Workarounds</span></span>

<span data-ttu-id="9d796-122">Pour convertir un littéral `Date` dans le format de vos paramètres régionaux ou dans un format personnalisé, fournissez le littéral à la fonction <xref:Microsoft.VisualBasic.Strings.Format%2A>, en spécifiant un format de date prédéfini ou défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d796-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="9d796-123">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="9d796-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="9d796-124">Vous pouvez également utiliser un des constructeurs surchargés de la structure <xref:System.DateTime> pour assembler une valeur de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="9d796-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="9d796-125">L'exemple suivant crée une valeur pour représenter le 31 mai 1993 à 12h14.</span><span class="sxs-lookup"><span data-stu-id="9d796-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="9d796-126">Format d'heure</span><span class="sxs-lookup"><span data-stu-id="9d796-126">Hour Format</span></span>

<span data-ttu-id="9d796-127">Vous pouvez spécifier la valeur d'heure dans un format de 12 heures ou de 24 heures, par exemple `#1:15:30 PM#` ou `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="9d796-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="9d796-128">Toutefois, si vous ne spécifiez pas les minutes ou les secondes, vous devez spécifier AM ou PM.</span><span class="sxs-lookup"><span data-stu-id="9d796-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="9d796-129">Valeurs par défaut de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="9d796-129">Date and Time Defaults</span></span>

<span data-ttu-id="9d796-130">Si vous n'incluez pas de date dans un littéral de date/heure, Visual Basic définit la partie date de la valeur sur le 1er janvier 0001.</span><span class="sxs-lookup"><span data-stu-id="9d796-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="9d796-131">Si vous n'incluez pas d'heure dans un littéral de date/heure, Visual Basic définit la partie heure de la valeur sur le début de la journée, c'est-à-dire minuit (0:00:00).</span><span class="sxs-lookup"><span data-stu-id="9d796-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="9d796-132">Conversions de type</span><span class="sxs-lookup"><span data-stu-id="9d796-132">Type Conversions</span></span>

<span data-ttu-id="9d796-133">Si vous convertissez une valeur `Date` vers le type `String`, Visual Basic restitue la date en fonction du format de date courte spécifié par les paramètres régionaux d'exécution, et restitue l'heure en fonction du format d'heure (12 heures ou 24 heures) spécifié par les paramètres régionaux d'exécution.</span><span class="sxs-lookup"><span data-stu-id="9d796-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="9d796-134">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="9d796-134">Programming Tips</span></span>

- <span data-ttu-id="9d796-135">**Considérations sur l'interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="9d796-135">**Interop Considerations.**</span></span> <span data-ttu-id="9d796-136">Si vous utilisez des composants non écrits pour le .NET Framework, tels que des objets Automation ou COM, n'oubliez pas que les types de date et d'heure utilisés dans les autres environnements ne sont pas compatibles avec le type `Date` de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9d796-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="9d796-137">Si vous transmettez un argument de date et d’heure à un tel composant, déclarez-le en tant que `Double` et non `Date` dans votre nouveau code Visual Basic, et utilisez les méthodes de conversion <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> et <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d796-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="9d796-138">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="9d796-138">**Type Characters.**</span></span> <span data-ttu-id="9d796-139">`Date`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="9d796-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="9d796-140">Toutefois, le compilateur traite les littéraux compris entre des signes dièse (`# #`) en tant que `Date`.</span><span class="sxs-lookup"><span data-stu-id="9d796-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="9d796-141">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="9d796-141">**Framework Type.**</span></span> <span data-ttu-id="9d796-142">Le type correspondant dans le .NET Framework est la structure <xref:System.DateTime?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d796-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="9d796-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d796-143">Example</span></span>

<span data-ttu-id="9d796-144">Une variable ou une constante du type de données `Date` contient à la fois la date et l'heure.</span><span class="sxs-lookup"><span data-stu-id="9d796-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="9d796-145">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="9d796-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="9d796-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d796-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="9d796-147">Types de données</span><span class="sxs-lookup"><span data-stu-id="9d796-147">Data Types</span></span>](index.md)
- [<span data-ttu-id="9d796-148">Chaînes de format de date et d’heure standard</span><span class="sxs-lookup"><span data-stu-id="9d796-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="9d796-149">Chaînes de format de date et d’heure personnalisées</span><span class="sxs-lookup"><span data-stu-id="9d796-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="9d796-150">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="9d796-150">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="9d796-151">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="9d796-151">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="9d796-152">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="9d796-152">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
