---
title: <typeparamref>-Guide de programmation C#
description: En savoir plus sur la <typeparamref> balise XML. Cette balise permet aux consommateurs du fichier de documentation de mettre en forme le mot d’une manière distincte, par exemple en italique.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380720"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="00de6-104">\<typeparamref>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="00de6-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="00de6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00de6-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="00de6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00de6-106">Parameters</span></span>

- `name`

  <span data-ttu-id="00de6-107">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="00de6-107">The name of the type parameter.</span></span> <span data-ttu-id="00de6-108">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="00de6-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="00de6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="00de6-109">Remarks</span></span>

<span data-ttu-id="00de6-110">Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="00de6-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="00de6-111">Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.</span><span class="sxs-lookup"><span data-stu-id="00de6-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="00de6-112">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="00de6-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="00de6-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="00de6-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="00de6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00de6-114">See also</span></span>

- [<span data-ttu-id="00de6-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="00de6-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="00de6-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="00de6-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
