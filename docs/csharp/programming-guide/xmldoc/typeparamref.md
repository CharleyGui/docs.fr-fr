---
title: <typeparamref>- Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789660"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="e7e22-102">\<typeparamref> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="e7e22-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7e22-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7e22-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="e7e22-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e7e22-104">Parameters</span></span>

- `name`

  <span data-ttu-id="e7e22-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="e7e22-105">The name of the type parameter.</span></span> <span data-ttu-id="e7e22-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="e7e22-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="e7e22-107">Notes </span><span class="sxs-lookup"><span data-stu-id="e7e22-107">Remarks</span></span>

<span data-ttu-id="e7e22-108">Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7e22-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="e7e22-109">Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.</span><span class="sxs-lookup"><span data-stu-id="e7e22-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="e7e22-110">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="e7e22-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e7e22-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e7e22-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="e7e22-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7e22-112">See also</span></span>

- [<span data-ttu-id="e7e22-113">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="e7e22-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e7e22-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e7e22-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
