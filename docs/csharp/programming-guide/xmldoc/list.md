---
title: <list> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789753"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="72540-102">> de la listeC# de \<(Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="72540-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="72540-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72540-103">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="72540-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="72540-104">Parameters</span></span>

- `term`

  <span data-ttu-id="72540-105">Terme à définir, qui est défini dans `description`.</span><span class="sxs-lookup"><span data-stu-id="72540-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="72540-106">Élément contenu dans une puce ou une liste numérotée ou définition d’un `term`.</span><span class="sxs-lookup"><span data-stu-id="72540-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="72540-107">Notes</span><span class="sxs-lookup"><span data-stu-id="72540-107">Remarks</span></span>

<span data-ttu-id="72540-108">Le bloc \<listheader> permet de définir la ligne d’en-tête d’une table ou d’une liste de définitions.</span><span class="sxs-lookup"><span data-stu-id="72540-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="72540-109">Au moment de définir une table, il vous suffit de fournir une entrée pour le terme figurant dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="72540-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="72540-110">Chaque élément de la liste est spécifié avec un bloc \<item>.</span><span class="sxs-lookup"><span data-stu-id="72540-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="72540-111">Au moment de créer une liste de définitions, vous devez spécifier à la fois `term` et `description`.</span><span class="sxs-lookup"><span data-stu-id="72540-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="72540-112">Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.</span><span class="sxs-lookup"><span data-stu-id="72540-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="72540-113">Une liste ou une table peut comporter autant de blocs \<item> que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="72540-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="72540-114">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="72540-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="72540-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="72540-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="72540-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72540-116">See also</span></span>

- [<span data-ttu-id="72540-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="72540-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="72540-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="72540-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
