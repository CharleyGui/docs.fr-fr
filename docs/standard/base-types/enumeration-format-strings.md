---
title: Chaînes de format d’énumération
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: c32fd9d59f61b6befe94ff9eb85b0c39ce926adb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348265"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="7b559-102">Chaînes de format d’énumération</span><span class="sxs-lookup"><span data-stu-id="7b559-102">Enumeration format strings</span></span>

<span data-ttu-id="7b559-103">Vous pouvez utiliser la méthode <xref:System.Enum.ToString%2A?displayProperty=nameWithType> pour créer un objet de chaîne qui représente la valeur numérique, hexadécimale ou de chaîne d’un membre d’énumération.</span><span class="sxs-lookup"><span data-stu-id="7b559-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="7b559-104">Cette méthode prend l’une des chaînes de mise en forme d’énumération pour spécifier la valeur à retourner.</span><span class="sxs-lookup"><span data-stu-id="7b559-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="7b559-105">Les sections suivantes répertorient les chaînes de mise en forme d’énumération et les valeurs qu’elles retournent.</span><span class="sxs-lookup"><span data-stu-id="7b559-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="7b559-106">Ces spécificateurs de format ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="7b559-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="7b559-107">G ou g</span><span class="sxs-lookup"><span data-stu-id="7b559-107">G or g</span></span>

<span data-ttu-id="7b559-108">Affiche l’entrée d’énumération comme valeur de chaîne, dans la mesure du possible ; sinon, affiche la valeur entière de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="7b559-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="7b559-109">Si l’énumération est définie avec l’attribut **Flags** défini, les valeurs de chaîne de chaque entrée valide sont concaténées et séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7b559-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7b559-110">Si l’attribut **Flags** n’est pas défini, une valeur non valide s’affiche comme entrée numérique.</span><span class="sxs-lookup"><span data-stu-id="7b559-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="7b559-111">L’exemple suivant illustre le spécificateur de format G.</span><span class="sxs-lookup"><span data-stu-id="7b559-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="7b559-112">F ou f</span><span class="sxs-lookup"><span data-stu-id="7b559-112">F or f</span></span>

<span data-ttu-id="7b559-113">Affiche l’entrée d’énumération comme valeur de chaîne, si possible.</span><span class="sxs-lookup"><span data-stu-id="7b559-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="7b559-114">Si la valeur peut être complètement affichée comme somme des entrées de l’énumération (même si l’attribut **Flags** n’est pas présent), les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7b559-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7b559-115">Si la valeur ne peut pas être complètement déterminée par les entrées de l’énumération, la valeur est mise en forme comme valeur entière.</span><span class="sxs-lookup"><span data-stu-id="7b559-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="7b559-116">L’exemple suivant illustre le spécificateur de format F.</span><span class="sxs-lookup"><span data-stu-id="7b559-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="7b559-117">D ou d</span><span class="sxs-lookup"><span data-stu-id="7b559-117">D or d</span></span>

<span data-ttu-id="7b559-118">Affiche l’entrée d’énumération comme valeur entière dans la représentation la plus courte possible.</span><span class="sxs-lookup"><span data-stu-id="7b559-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="7b559-119">L’exemple suivant illustre le spécificateur de format D.</span><span class="sxs-lookup"><span data-stu-id="7b559-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="7b559-120">X ou x</span><span class="sxs-lookup"><span data-stu-id="7b559-120">X or x</span></span>

<span data-ttu-id="7b559-121">Affiche l’entrée d’énumération comme valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="7b559-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="7b559-122">La valeur est représentée avec des zéros interligne si nécessaire, pour vérifier que la chaîne de résultat a deux caractères pour chaque octet dans le [type numérique sous-jacent](xref:System.Enum.GetUnderlyingType%2A) du type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="7b559-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="7b559-123">L’exemple suivant illustre le spécificateur de format X.</span><span class="sxs-lookup"><span data-stu-id="7b559-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="7b559-124">Dans l’exemple, le type sous-jacent des deux <xref:System.ConsoleColor> et <xref:System.IO.FileAttributes> est <xref:System.Int32> ou un entier de 32 bits (ou 4 octets), ce qui produit une chaîne de résultat de 8 caractères.</span><span class="sxs-lookup"><span data-stu-id="7b559-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="7b559-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b559-125">Example</span></span>

<span data-ttu-id="7b559-126">L’exemple suivant définit une énumération appelée `Colors` qui se compose de trois entrées : `Red`, `Blue` et `Green`.</span><span class="sxs-lookup"><span data-stu-id="7b559-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="7b559-127">Une fois que l’énumération est définie, une instance peut être déclarée de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="7b559-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="7b559-128">La méthode `Color.ToString(System.String)` peut ensuite être utilisée pour afficher la valeur d’énumération de différentes manières, selon le spécificateur de format qui lui est passé.</span><span class="sxs-lookup"><span data-stu-id="7b559-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="7b559-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b559-129">See also</span></span>

- [<span data-ttu-id="7b559-130">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="7b559-130">Formatting Types</span></span>](formatting-types.md)
