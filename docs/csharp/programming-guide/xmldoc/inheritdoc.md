---
title: <inheritdoc> - Guide de programmation C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 8c416275254892efdb9f15cd2ae0af5634c82357
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184090"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="9ea37-102">\<inheritdoc> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9ea37-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ea37-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea37-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="9ea37-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="9ea37-104">InheritDoc</span></span>

<span data-ttu-id="9ea37-105">Hériter des commentaires XML à partir des classes de base, des interfaces et des méthodes similaires.</span><span class="sxs-lookup"><span data-stu-id="9ea37-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="9ea37-106">Cela élimine la copie et le collage indésirables de commentaires XML en double et conserve automatiquement les commentaires XML synchronisés.</span><span class="sxs-lookup"><span data-stu-id="9ea37-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9ea37-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9ea37-107">Remarks</span></span>  

<span data-ttu-id="9ea37-108">Ajoutez vos commentaires XML dans des classes ou des interfaces de base et laissez InheritDoc copier les commentaires vers les classes d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="9ea37-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="9ea37-109">Ajoutez vos commentaires XML à vos méthodes synchrones et laissez InheritDoc copier les commentaires dans vos versions asynchrones des mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="9ea37-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="9ea37-110">Si vous souhaitez copier les commentaires à partir d’un membre spécifique, vous pouvez utiliser l' `cref` attribut pour spécifier le membre.</span><span class="sxs-lookup"><span data-stu-id="9ea37-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="9ea37-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="9ea37-111">Examples</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="9ea37-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ea37-112">See also</span></span>

- [<span data-ttu-id="9ea37-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9ea37-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ea37-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="9ea37-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
