---
title: <remarks> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 2391a8ee0bb55402ff5183c837e36d04a39e6555
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711699"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="dc8db-102">\<remarks> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="dc8db-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="dc8db-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc8db-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc8db-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="dc8db-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="dc8db-105">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="dc8db-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc8db-106">Notes</span><span class="sxs-lookup"><span data-stu-id="dc8db-106">Remarks</span></span>  
 <span data-ttu-id="dc8db-107">La balise \<remarks> permet d’ajouter des informations sur un type en complétant les informations spécifiées par [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="dc8db-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="dc8db-108">Ces informations sont affichées dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="dc8db-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="dc8db-109">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="dc8db-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8db-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc8db-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="dc8db-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc8db-111">See also</span></span>

- [<span data-ttu-id="dc8db-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="dc8db-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc8db-113">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="dc8db-113">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
