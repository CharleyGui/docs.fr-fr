---
title: <c>-Guide de programmation C#
description: En savoir plus sur la <c> balise XML. Cette balise marque un texte sur une seule ligne dans une description comme du code, alors que <code>indicates multiple lines.
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382020"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="8cb5b-104">\<c>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8cb5b-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cb5b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cb5b-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="8cb5b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8cb5b-106">Parameters</span></span>

- `text`

  <span data-ttu-id="8cb5b-107">Texte que vous souhaitez indiquer comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cb5b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="8cb5b-108">Remarks</span></span>

<span data-ttu-id="8cb5b-109">La `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="8cb5b-110">Utilisez [\<code>](./code.md) pour indiquer plusieurs lignes en tant que code.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="8cb5b-111">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8cb5b-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="8cb5b-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="8cb5b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cb5b-113">See also</span></span>

- [<span data-ttu-id="8cb5b-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8cb5b-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8cb5b-115">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="8cb5b-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
