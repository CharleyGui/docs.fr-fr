---
title: <remarks> - Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793370"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="256e9-102">\<remarques> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="256e9-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="256e9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="256e9-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="256e9-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="256e9-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="256e9-105">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="256e9-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="256e9-106">Notes </span><span class="sxs-lookup"><span data-stu-id="256e9-106">Remarks</span></span>

<span data-ttu-id="256e9-107">Les \<remarques> tag est utilisé pour ajouter des informations sur un type, complétant l’information spécifiée avec [ \<des>sommaires ](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="256e9-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="256e9-108">Ces informations sont affichées dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="256e9-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="256e9-109">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="256e9-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="256e9-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="256e9-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="256e9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="256e9-111">See also</span></span>

- [<span data-ttu-id="256e9-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="256e9-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="256e9-113">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="256e9-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
