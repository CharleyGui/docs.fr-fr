---
title: <remarks> -Guide de programmation C#
description: En savoir plus sur le XML <remarks> balise. Cette balise est utilisée pour ajouter des informations sur un type, en complétant les informations spécifiées avec <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381500"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="1ab60-106">\<remarks>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1ab60-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab60-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ab60-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="1ab60-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ab60-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="1ab60-109">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="1ab60-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ab60-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1ab60-110">Remarks</span></span>

<span data-ttu-id="1ab60-111">La `<remarks>` balise est utilisée pour ajouter des informations sur un type et compléter les informations spécifiées par [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="1ab60-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="1ab60-112">Ces informations sont affichées dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="1ab60-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="1ab60-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="1ab60-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1ab60-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ab60-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="1ab60-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ab60-115">See also</span></span>

- [<span data-ttu-id="1ab60-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1ab60-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1ab60-117">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="1ab60-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
