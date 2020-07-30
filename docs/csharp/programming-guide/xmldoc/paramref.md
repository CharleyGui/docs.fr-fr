---
title: <paramref>-Guide de programmation C#
description: En savoir plus sur la <paramref> balise XML. Cette balise vous donne un moyen d’indiquer qu’un mot du code est un paramètre.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381838"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="47d3b-104">\<paramref>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="47d3b-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="47d3b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47d3b-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="47d3b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47d3b-106">Parameters</span></span>

- `name`

  <span data-ttu-id="47d3b-107">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="47d3b-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="47d3b-108">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="47d3b-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="47d3b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="47d3b-109">Remarks</span></span>

<span data-ttu-id="47d3b-110">La `<paramref>` balise vous donne un moyen d’indiquer qu’un mot dans les commentaires de code, par exemple dans un `<summary>` `<remarks>` bloc ou fait référence à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="47d3b-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="47d3b-111">Le fichier XML peut être traité de manière à mettre en forme ce mot d’une façon particulière, par exemple en gras ou en italique.</span><span class="sxs-lookup"><span data-stu-id="47d3b-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="47d3b-112">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="47d3b-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="47d3b-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="47d3b-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="47d3b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47d3b-114">See also</span></span>

- [<span data-ttu-id="47d3b-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="47d3b-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="47d3b-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="47d3b-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
