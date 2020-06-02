---
title: <c>-Guide de programmation C#
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287465"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="c0364-102">\<c>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c0364-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0364-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0364-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="c0364-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0364-104">Parameters</span></span>

- `text`

  <span data-ttu-id="c0364-105">Texte que vous souhaitez indiquer comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="c0364-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0364-106">Notes</span><span class="sxs-lookup"><span data-stu-id="c0364-106">Remarks</span></span>

<span data-ttu-id="c0364-107">La `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="c0364-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="c0364-108">Utilisez [\<code>](./code.md) pour indiquer plusieurs lignes en tant que code.</span><span class="sxs-lookup"><span data-stu-id="c0364-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="c0364-109">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c0364-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c0364-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0364-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="c0364-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0364-111">See also</span></span>

- [<span data-ttu-id="c0364-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c0364-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c0364-113">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c0364-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
