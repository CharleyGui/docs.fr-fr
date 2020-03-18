---
title: <returns> - Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789709"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="e5645-102">\<retours> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="e5645-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5645-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5645-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="e5645-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5645-104">Parameters</span></span>

- `description`

  <span data-ttu-id="e5645-105">Description de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="e5645-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5645-106">Notes </span><span class="sxs-lookup"><span data-stu-id="e5645-106">Remarks</span></span>

<span data-ttu-id="e5645-107">La balise \<returns> doit être utilisée dans le commentaire relatif à une déclaration de méthode pour décrire la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="e5645-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="e5645-108">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="e5645-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e5645-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e5645-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="e5645-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5645-110">See also</span></span>

- [<span data-ttu-id="e5645-111">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="e5645-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e5645-112">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e5645-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
