---
title: Diviser des chaînes à l’aide de String. Split (Guide C#)
description: La méthode Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple d’extraire des sous-chaînes d’une chaîne.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 5361a3c60905edd19b180c5ddb14064a85f64337
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400498"
---
# <a name="how-to-separate-strings-using-stringsplit-in-c"></a><span data-ttu-id="f513b-104">Comment séparer des chaînes à l’aide de String. Split en C\#</span><span class="sxs-lookup"><span data-stu-id="f513b-104">How to separate strings using String.Split in C\#</span></span>

<span data-ttu-id="f513b-105">La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="f513b-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="f513b-106">Cette méthode est souvent le moyen le plus simple de séparer une chaîne sur les limites de mots.</span><span class="sxs-lookup"><span data-stu-id="f513b-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="f513b-107">Il est également utilisé pour fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f513b-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="f513b-108">Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.</span><span class="sxs-lookup"><span data-stu-id="f513b-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="f513b-109">Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="f513b-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="f513b-110">Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="f513b-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="f513b-111">Vous pouvez voir comment une chaîne vide est créée dans l’exemple suivant, qui utilise le caractère espace comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="f513b-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="f513b-112">Ce comportement facilite l’utilisation de formats tels que des fichiers de valeurs séparées par des virgules (CSV) représentant des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="f513b-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="f513b-113">Les virgules consécutives représentent une colonne vide.</span><span class="sxs-lookup"><span data-stu-id="f513b-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="f513b-114">Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> facultatif pour exclure toutes les chaînes vides dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="f513b-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="f513b-115">Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.</span><span class="sxs-lookup"><span data-stu-id="f513b-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="f513b-116"><xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.</span><span class="sxs-lookup"><span data-stu-id="f513b-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="f513b-117">L’exemple suivant utilise des espaces, des virgules, des points, des deux-points et des tabulations comme séparateurs de caractères, qui sont passés à <xref:System.String.Split%2A> dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="f513b-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="f513b-118">La boucle en bas du code affiche chacun des mots dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="f513b-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="f513b-119">Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :</span><span class="sxs-lookup"><span data-stu-id="f513b-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="f513b-120"><xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).</span><span class="sxs-lookup"><span data-stu-id="f513b-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="f513b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f513b-121">See also</span></span>

- [<span data-ttu-id="f513b-122">Extraire des éléments d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="f513b-122">Extract elements from a string</span></span>](../../standard/base-types/divide-up-strings.md)
- [<span data-ttu-id="f513b-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f513b-123">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="f513b-124">Chaînes</span><span class="sxs-lookup"><span data-stu-id="f513b-124">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="f513b-125">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="f513b-125">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
