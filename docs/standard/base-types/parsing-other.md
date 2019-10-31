---
title: Analyse d’autres chaînes dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127570"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="9e93b-102">Analyse d’autres chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="9e93b-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="9e93b-103">Outre des chaînes numériques et <xref:System.DateTime>, vous pouvez analyser des chaînes qui représentent les types <xref:System.Char>, <xref:System.Boolean> et <xref:System.Enum> dans des types de données.</span><span class="sxs-lookup"><span data-stu-id="9e93b-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="9e93b-104">Char</span><span class="sxs-lookup"><span data-stu-id="9e93b-104">Char</span></span>  
 <span data-ttu-id="9e93b-105">La méthode d’analyse statique associée au type de données **Char** est utile pour la conversion d’une chaîne qui contient un caractère unique en une valeur Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e93b-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="9e93b-106">L’exemple de code suivant analyse une chaîne en un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e93b-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="9e93b-107">Booléen</span><span class="sxs-lookup"><span data-stu-id="9e93b-107">Boolean</span></span>  
 <span data-ttu-id="9e93b-108">Le type de données **Boolean** contient une méthode **Parse** que vous pouvez utiliser pour convertir une chaîne représentant une valeur Boolean en type **Boolean** réel.</span><span class="sxs-lookup"><span data-stu-id="9e93b-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="9e93b-109">Cette méthode ne respecte pas la casse et peut analyser une chaîne contenant « True » ou « False ».</span><span class="sxs-lookup"><span data-stu-id="9e93b-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="9e93b-110">La méthode **Parse** associée au type **Boolean** peut aussi analyser des chaînes entourées d’espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="9e93b-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="9e93b-111">Si une autre chaîne est passée, une exception <xref:System.FormatException> est levée.</span><span class="sxs-lookup"><span data-stu-id="9e93b-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="9e93b-112">L’exemple de code suivant utilise la méthode **Parse** pour convertir une chaîne en valeur Boolean.</span><span class="sxs-lookup"><span data-stu-id="9e93b-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="9e93b-113">Énumération</span><span class="sxs-lookup"><span data-stu-id="9e93b-113">Enumeration</span></span>  
 <span data-ttu-id="9e93b-114">Vous pouvez utiliser la méthode **Parse** statique pour initialiser un type d’énumération avec la valeur d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9e93b-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="9e93b-115">Cette méthode accepte le type d’énumération que vous analysez, la chaîne à analyser et un indicateur Boolean facultatif indiquant si l’analyse respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="9e93b-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="9e93b-116">La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d’un ou plusieurs espaces vides (aussi appelés espaces blancs).</span><span class="sxs-lookup"><span data-stu-id="9e93b-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="9e93b-117">Quand la chaîne contient plusieurs valeurs, celle de l’objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération OR au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="9e93b-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="9e93b-118">L’exemple suivant utilise la méthode **Parse** pour convertir une représentation sous forme de chaîne en valeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="9e93b-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="9e93b-119">L’énumération <xref:System.DayOfWeek> est initialisée à **Thursday** à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9e93b-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9e93b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e93b-120">See also</span></span>

- [<span data-ttu-id="9e93b-121">Analyse de chaînes</span><span class="sxs-lookup"><span data-stu-id="9e93b-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)
- [<span data-ttu-id="9e93b-122">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="9e93b-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
- [<span data-ttu-id="9e93b-123">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="9e93b-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
