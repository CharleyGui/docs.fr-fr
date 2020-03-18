---
title: Comment analyser les cordes à l’aide de String.Split (Guide C)
description: String.Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple pour analyser des chaînes.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973233"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="d21b6-104">Comment analyser les cordes à l’aide de String.Split (Guide C)</span><span class="sxs-lookup"><span data-stu-id="d21b6-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="d21b6-105">La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="d21b6-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="d21b6-106">C’est souvent le moyen le plus simple pour séparer une chaîne sur des limites de mots.</span><span class="sxs-lookup"><span data-stu-id="d21b6-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="d21b6-107">Elle sert également à fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d21b6-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d21b6-108">Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.</span><span class="sxs-lookup"><span data-stu-id="d21b6-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="d21b6-109">Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="d21b6-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="d21b6-110">Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="d21b6-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="d21b6-111">Vous pouvez l’observer dans l’exemple suivant, qui utilise l’espace comme séparateur :</span><span class="sxs-lookup"><span data-stu-id="d21b6-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="d21b6-112">Ce comportement facilite l’utilisation de formats tels que les fichiers CSV (valeurs séparées par des virgules) représentant des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="d21b6-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="d21b6-113">Les virgules consécutives représentent une colonne vide.</span><span class="sxs-lookup"><span data-stu-id="d21b6-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="d21b6-114">Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> facultatif pour exclure toutes les chaînes vides dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="d21b6-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="d21b6-115">Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.</span><span class="sxs-lookup"><span data-stu-id="d21b6-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="d21b6-116"><xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.</span><span class="sxs-lookup"><span data-stu-id="d21b6-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="d21b6-117">L’exemple suivant utilise des caractères de séparation (espaces, virgules, points, deux-points et onglets) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="d21b6-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="d21b6-118">La boucle en bas du code affiche chacun des mots dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="d21b6-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="d21b6-119">Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :</span><span class="sxs-lookup"><span data-stu-id="d21b6-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="d21b6-120"><xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).</span><span class="sxs-lookup"><span data-stu-id="d21b6-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="d21b6-121">Vous pouvez essayer ces échantillons en regardant le code dans notre [référentiel GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="d21b6-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="d21b6-122">Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="d21b6-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="d21b6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d21b6-123">See also</span></span>

- [<span data-ttu-id="d21b6-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d21b6-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="d21b6-125">Cordes</span><span class="sxs-lookup"><span data-stu-id="d21b6-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="d21b6-126">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="d21b6-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
