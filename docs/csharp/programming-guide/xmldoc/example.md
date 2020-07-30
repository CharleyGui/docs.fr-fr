---
title: <example> -Guide de programmation C#
description: En savoir plus sur le XML <example> balise. Cette balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381526"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="a623f-105">\<example>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a623f-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a623f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a623f-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="a623f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a623f-107">Parameters</span></span>

- `description`

  <span data-ttu-id="a623f-108">Description de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="a623f-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="a623f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a623f-109">Remarks</span></span>

<span data-ttu-id="a623f-110">La `<example>` balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a623f-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="a623f-111">Cela implique généralement l’utilisation de la [\<code>](./code.md) balise.</span><span class="sxs-lookup"><span data-stu-id="a623f-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="a623f-112">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="a623f-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a623f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a623f-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="a623f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a623f-114">See also</span></span>

- [<span data-ttu-id="a623f-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a623f-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a623f-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="a623f-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
