---
title: <returns> -Guide de programmation C#
description: En savoir plus sur le XML <returns> balise. Cette balise est utilisée dans le commentaire d’une déclaration de méthode pour décrire la valeur de retour.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381396"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="c864c-105">\<returns>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c864c-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c864c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c864c-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="c864c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c864c-107">Parameters</span></span>

- `description`

  <span data-ttu-id="c864c-108">Description de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c864c-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="c864c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c864c-109">Remarks</span></span>

<span data-ttu-id="c864c-110">La `<returns>` balise doit être utilisée dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c864c-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="c864c-111">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c864c-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c864c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c864c-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="c864c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c864c-113">See also</span></span>

- [<span data-ttu-id="c864c-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c864c-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c864c-115">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c864c-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
