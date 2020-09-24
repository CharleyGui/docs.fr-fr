---
title: Comment déterminer si une chaîne représente une valeur numérique-Guide de programmation C#
description: Découvrez comment déterminer si une chaîne est une représentation valide d’un type numérique spécifié. Consultez des exemples de code et affichez des ressources supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: cbe0703ca39422ac0a9e7a93bf2cfc4c3f8528f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151426"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="a35f6-104">Comment déterminer si une chaîne représente une valeur numérique (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a35f6-104">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>

<span data-ttu-id="a35f6-105">Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="a35f6-105">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="a35f6-106">L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../language-reference/builtin-types/integral-numeric-types.md) valide.</span><span class="sxs-lookup"><span data-stu-id="a35f6-106">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="a35f6-107">Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="a35f6-107">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="a35f6-108">Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.</span><span class="sxs-lookup"><span data-stu-id="a35f6-108">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a35f6-109">Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="a35f6-109">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="a35f6-110">Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`.</span><span class="sxs-lookup"><span data-stu-id="a35f6-110">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="a35f6-111">« 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a35f6-111">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a35f6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="a35f6-112">Example</span></span>  

 <span data-ttu-id="a35f6-113">Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="a35f6-113">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a35f6-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="a35f6-114">Robust Programming</span></span>  

 <span data-ttu-id="a35f6-115">Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide.</span><span class="sxs-lookup"><span data-stu-id="a35f6-115">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="a35f6-116">`TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="a35f6-116">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a35f6-117">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="a35f6-117">.NET Security</span></span>  

 <span data-ttu-id="a35f6-118">Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a35f6-118">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35f6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a35f6-119">See also</span></span>

- [<span data-ttu-id="a35f6-120">Comment convertir un tableau d’octets en entier</span><span class="sxs-lookup"><span data-stu-id="a35f6-120">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="a35f6-121">Comment convertir une chaîne en nombre</span><span class="sxs-lookup"><span data-stu-id="a35f6-121">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="a35f6-122">Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques</span><span class="sxs-lookup"><span data-stu-id="a35f6-122">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="a35f6-123">Analyse des chaînes numériques</span><span class="sxs-lookup"><span data-stu-id="a35f6-123">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="a35f6-124">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="a35f6-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
