---
title: <remarks> - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 822ca8feafe48402f8217c10ef37fcdb1576c27a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587752"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="395da-102">\<remarks> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="395da-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="395da-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="395da-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="395da-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="395da-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="395da-105">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="395da-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="395da-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="395da-106">Remarks</span></span>  
 <span data-ttu-id="395da-107">La balise \<remarks> permet d’ajouter des informations sur un type en complétant les informations spécifiées par [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="395da-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="395da-108">Ces informations sont affichées dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="395da-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="395da-109">Compilez avec [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="395da-109">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="395da-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="395da-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="395da-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="395da-111">See also</span></span>

- [<span data-ttu-id="395da-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="395da-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="395da-113">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="395da-113">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
