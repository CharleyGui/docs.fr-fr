---
title: <typeparamref> - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: f01df27b920dcf3011a51015c771d2da3b442c4c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587433"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="1b9b7-102">\<typeparamref> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1b9b7-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1b9b7-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b9b7-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b9b7-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b9b7-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1b9b7-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="1b9b7-105">The name of the type parameter.</span></span> <span data-ttu-id="1b9b7-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="1b9b7-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b9b7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b9b7-107">Remarks</span></span>  
 <span data-ttu-id="1b9b7-108">Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="1b9b7-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="1b9b7-109">Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.</span><span class="sxs-lookup"><span data-stu-id="1b9b7-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="1b9b7-110">Compilez avec [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="1b9b7-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9b7-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="1b9b7-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="1b9b7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b9b7-112">See also</span></span>

- [<span data-ttu-id="1b9b7-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1b9b7-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1b9b7-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="1b9b7-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
