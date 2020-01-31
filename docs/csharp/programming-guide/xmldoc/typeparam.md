---
title: <typeparam> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793365"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="3a877-102">\<typeparam > (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="3a877-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a877-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a877-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="3a877-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="3a877-104">Parameters</span></span>

- `name`

  <span data-ttu-id="3a877-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="3a877-105">The name of the type parameter.</span></span> <span data-ttu-id="3a877-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="3a877-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="3a877-107">Description du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="3a877-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a877-108">Notes</span><span class="sxs-lookup"><span data-stu-id="3a877-108">Remarks</span></span>

<span data-ttu-id="3a877-109">La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="3a877-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="3a877-110">Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.</span><span class="sxs-lookup"><span data-stu-id="3a877-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="3a877-111">Pour plus d’informations, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a877-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="3a877-112">Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="3a877-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="3a877-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3a877-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="3a877-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a877-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="3a877-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a877-115">See also</span></span>

- [<span data-ttu-id="3a877-116">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="3a877-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3a877-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3a877-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="3a877-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="3a877-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
