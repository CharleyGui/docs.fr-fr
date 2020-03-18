---
title: Comment déterminer si une chaîne représente une valeur numérique - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157063"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="bade4-102">Comment déterminer si une chaîne représente une valeur numérique (Guide de programmation CMD)</span><span class="sxs-lookup"><span data-stu-id="bade4-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="bade4-103">Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="bade4-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="bade4-104">L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../language-reference/builtin-types/integral-numeric-types.md) valide.</span><span class="sxs-lookup"><span data-stu-id="bade4-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="bade4-105">Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="bade4-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="bade4-106">Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="bade4-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bade4-107">Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="bade4-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="bade4-108">Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`.</span><span class="sxs-lookup"><span data-stu-id="bade4-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="bade4-109">« 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.</span><span class="sxs-lookup"><span data-stu-id="bade4-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bade4-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="bade4-110">Example</span></span>  
 <span data-ttu-id="bade4-111">Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="bade4-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bade4-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="bade4-112">Robust Programming</span></span>  
 <span data-ttu-id="bade4-113">Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide.</span><span class="sxs-lookup"><span data-stu-id="bade4-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="bade4-114">`TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bade4-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bade4-115">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bade4-115">.NET Framework Security</span></span>  
 <span data-ttu-id="bade4-116">Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="bade4-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bade4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bade4-117">See also</span></span>

- [<span data-ttu-id="bade4-118">Comment convertir un tableau d’octets en entier</span><span class="sxs-lookup"><span data-stu-id="bade4-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="bade4-119">Comment convertir une chaîne en nombre</span><span class="sxs-lookup"><span data-stu-id="bade4-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="bade4-120">Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques</span><span class="sxs-lookup"><span data-stu-id="bade4-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="bade4-121">Parsing Chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="bade4-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="bade4-122">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="bade4-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
