---
title: <list> - Guide de programmation C#
ms.custom: seodec18
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
ms.openlocfilehash: aadb24c43d49acb3e71490efd156b14d9fc5f133
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587976"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="6de95-102">\<list> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6de95-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6de95-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de95-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
## <a name="parameters"></a><span data-ttu-id="6de95-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6de95-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="6de95-105">Terme à définir, qui est défini dans `description`.</span><span class="sxs-lookup"><span data-stu-id="6de95-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="6de95-106">Élément contenu dans une puce ou une liste numérotée ou définition d’un `term`.</span><span class="sxs-lookup"><span data-stu-id="6de95-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de95-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="6de95-107">Remarks</span></span>  
 <span data-ttu-id="6de95-108">Le bloc \<listheader> permet de définir la ligne d’en-tête d’une table ou d’une liste de définitions.</span><span class="sxs-lookup"><span data-stu-id="6de95-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="6de95-109">Au moment de définir une table, il vous suffit de fournir une entrée pour le terme figurant dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="6de95-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="6de95-110">Chaque élément de la liste est spécifié avec un bloc \<item>.</span><span class="sxs-lookup"><span data-stu-id="6de95-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="6de95-111">Au moment de créer une liste de définitions, vous devez spécifier à la fois `term` et `description`.</span><span class="sxs-lookup"><span data-stu-id="6de95-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="6de95-112">Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.</span><span class="sxs-lookup"><span data-stu-id="6de95-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="6de95-113">Une liste ou une table peut comporter autant de blocs \<item> que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6de95-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="6de95-114">Compilez avec [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="6de95-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6de95-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="6de95-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6de95-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de95-116">See also</span></span>

- [<span data-ttu-id="6de95-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6de95-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6de95-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="6de95-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
