---
title: Analyser des chaînes à l’aide de String. Split (Guide C#)
description: La méthode Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple pour analyser des chaînes.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 7c5d8fa462775c6f3a9981693129997dda6c2286
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324138"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="c75e6-104">Comment analyser des chaînes à l’aide de String. Split en C\#</span><span class="sxs-lookup"><span data-stu-id="c75e6-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="c75e6-105">La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="c75e6-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="c75e6-106">Cette méthode est souvent le moyen le plus simple de séparer une chaîne sur les limites de mots.</span><span class="sxs-lookup"><span data-stu-id="c75e6-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="c75e6-107">Il est également utilisé pour fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c75e6-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c75e6-108">Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.</span><span class="sxs-lookup"><span data-stu-id="c75e6-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="c75e6-109">Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="c75e6-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="c75e6-110">Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="c75e6-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="c75e6-111">Vous pouvez voir comment une chaîne vide est créée dans l’exemple suivant, qui utilise le caractère espace comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="c75e6-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="c75e6-112">Ce comportement facilite l’utilisation de formats tels que des fichiers de valeurs séparées par des virgules (CSV) représentant des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="c75e6-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="c75e6-113">Les virgules consécutives représentent une colonne vide.</span><span class="sxs-lookup"><span data-stu-id="c75e6-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="c75e6-114">Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> facultatif pour exclure toutes les chaînes vides dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="c75e6-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="c75e6-115">Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.</span><span class="sxs-lookup"><span data-stu-id="c75e6-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="c75e6-116"><xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.</span><span class="sxs-lookup"><span data-stu-id="c75e6-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="c75e6-117">L’exemple suivant utilise des espaces, des virgules, des points, des deux-points et des tabulations comme séparateurs de caractères, qui sont passés à <xref:System.String.Split%2A> dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="c75e6-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="c75e6-118">La boucle en bas du code affiche chacun des mots dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="c75e6-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="c75e6-119">Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :</span><span class="sxs-lookup"><span data-stu-id="c75e6-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="c75e6-120"><xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).</span><span class="sxs-lookup"><span data-stu-id="c75e6-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="c75e6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c75e6-121">See also</span></span>

- [<span data-ttu-id="c75e6-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c75e6-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="c75e6-123">Chaînes</span><span class="sxs-lookup"><span data-stu-id="c75e6-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="c75e6-124">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="c75e6-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
