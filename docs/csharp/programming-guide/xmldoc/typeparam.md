---
title: <typeparam> -Guide de programmation C#
description: En savoir plus sur le XML <typeparam> balise. Cette balise est utilisée dans le commentaire d’une déclaration de type ou de méthode générique pour décrire un paramètre de type.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380785"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="e538e-105">\<typeparam>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e538e-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e538e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e538e-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="e538e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e538e-107">Parameters</span></span>

- `name`

  <span data-ttu-id="e538e-108">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="e538e-108">The name of the type parameter.</span></span> <span data-ttu-id="e538e-109">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="e538e-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="e538e-110">Description du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="e538e-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="e538e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e538e-111">Remarks</span></span>

<span data-ttu-id="e538e-112">La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="e538e-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="e538e-113">Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.</span><span class="sxs-lookup"><span data-stu-id="e538e-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="e538e-114">Pour plus d’informations, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="e538e-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="e538e-115">Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="e538e-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="e538e-116">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="e538e-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e538e-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e538e-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="e538e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e538e-118">See also</span></span>

- [<span data-ttu-id="e538e-119">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="e538e-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e538e-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e538e-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e538e-121">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e538e-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
