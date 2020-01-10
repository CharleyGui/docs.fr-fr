---
title: <typeparamref> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 3e96d55d7cf60b2a9085cf065ef3b8193b173c5d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711673"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="919be-102">\<typeparamref> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="919be-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="919be-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="919be-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="919be-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="919be-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="919be-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="919be-105">The name of the type parameter.</span></span> <span data-ttu-id="919be-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="919be-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919be-107">Notes</span><span class="sxs-lookup"><span data-stu-id="919be-107">Remarks</span></span>  
 <span data-ttu-id="919be-108">Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="919be-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="919be-109">Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.</span><span class="sxs-lookup"><span data-stu-id="919be-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="919be-110">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="919be-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="919be-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="919be-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="919be-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="919be-112">See also</span></span>

- [<span data-ttu-id="919be-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="919be-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="919be-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="919be-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
