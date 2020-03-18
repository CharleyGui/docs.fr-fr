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
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156946"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="8d470-102">\<inheritdoc> (Guide de programmation de C)</span><span class="sxs-lookup"><span data-stu-id="8d470-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8d470-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d470-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="8d470-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="8d470-104">InheritDoc</span></span>

<span data-ttu-id="8d470-105">Héritez des commentaires XML des classes de base, des interfaces et des méthodes similaires.</span><span class="sxs-lookup"><span data-stu-id="8d470-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="8d470-106">Cela élimine la copie et le coller indésirables des commentaires XML en double et maintient automatiquement les commentaires XML synchronisés.</span><span class="sxs-lookup"><span data-stu-id="8d470-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8d470-107">Notes </span><span class="sxs-lookup"><span data-stu-id="8d470-107">Remarks</span></span>  
<span data-ttu-id="8d470-108">Ajoutez vos commentaires XML dans des classes de base ou des interfaces et laissez InheritDoc copier les commentaires aux classes de mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="8d470-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="8d470-109">Ajoutez vos commentaires XML à vos méthodes synchrones et laissez InheritDoc copier les commentaires à vos versions asynchrones des mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="8d470-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="8d470-110">Si vous souhaitez copier les commentaires d’un `cref` membre spécifique, vous pouvez utiliser l’attribut pour spécifier le membre.</span><span class="sxs-lookup"><span data-stu-id="8d470-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="8d470-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="8d470-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="8d470-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d470-112">See also</span></span>

- [<span data-ttu-id="8d470-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8d470-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8d470-114">Tags recommandés pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="8d470-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
