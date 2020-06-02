---
title: <returns> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287231"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="b1e53-102">\<returns>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b1e53-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1e53-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1e53-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="b1e53-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1e53-104">Parameters</span></span>

- `description`

  <span data-ttu-id="b1e53-105">Description de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b1e53-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1e53-106">Notes</span><span class="sxs-lookup"><span data-stu-id="b1e53-106">Remarks</span></span>

<span data-ttu-id="b1e53-107">La `<returns>` balise doit être utilisée dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b1e53-107">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="b1e53-108">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="b1e53-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b1e53-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1e53-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="b1e53-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1e53-110">See also</span></span>

- [<span data-ttu-id="b1e53-111">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b1e53-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b1e53-112">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="b1e53-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
