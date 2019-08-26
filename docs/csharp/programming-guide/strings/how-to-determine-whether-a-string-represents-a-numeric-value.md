---
title: 'Procédure : Déterminer si une chaîne représente une valeur numérique - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 831f0fc83c8a7066b40d64e4765a312b8b4847bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921780"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="413c5-102">Procédure : Déterminer si une chaîne représente une valeur numérique (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="413c5-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="413c5-103">Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="413c5-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="413c5-104">L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../language-reference/builtin-types/integral-numeric-types.md) valide.</span><span class="sxs-lookup"><span data-stu-id="413c5-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="413c5-105">Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="413c5-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="413c5-106">Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="413c5-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="413c5-107">Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="413c5-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="413c5-108">Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`.</span><span class="sxs-lookup"><span data-stu-id="413c5-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="413c5-109">« 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.</span><span class="sxs-lookup"><span data-stu-id="413c5-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="413c5-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="413c5-110">Example</span></span>  
 <span data-ttu-id="413c5-111">Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="413c5-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="413c5-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="413c5-112">Robust Programming</span></span>  
 <span data-ttu-id="413c5-113">Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide.</span><span class="sxs-lookup"><span data-stu-id="413c5-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="413c5-114">`TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="413c5-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="413c5-115">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="413c5-115">.NET Framework Security</span></span>  
 <span data-ttu-id="413c5-116">Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="413c5-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413c5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="413c5-117">See also</span></span>

- [<span data-ttu-id="413c5-118">Guide pratique pour convertir un tableau d’octets en int</span><span class="sxs-lookup"><span data-stu-id="413c5-118">How to: Convert a byte Array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="413c5-119">Guide pratique pour convertir une chaîne en nombre</span><span class="sxs-lookup"><span data-stu-id="413c5-119">How to: Convert a String to a Number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="413c5-120">Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques</span><span class="sxs-lookup"><span data-stu-id="413c5-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="413c5-121">Analyse de chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="413c5-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="413c5-122">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="413c5-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
