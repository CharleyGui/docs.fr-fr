---
title: <param> -Guide de programmation C#
description: En savoir plus sur le XML <param> balise. Cette balise est utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381552"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="15c98-105">\<param>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="15c98-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="15c98-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c98-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="15c98-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15c98-107">Parameters</span></span>

- `name`

  <span data-ttu-id="15c98-108">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="15c98-108">The name of a method parameter.</span></span> <span data-ttu-id="15c98-109">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="15c98-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="15c98-110">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="15c98-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="15c98-111">Notes</span><span class="sxs-lookup"><span data-stu-id="15c98-111">Remarks</span></span>

<span data-ttu-id="15c98-112">La `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="15c98-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="15c98-113">Pour documenter plusieurs paramètres, utilisez plusieurs `<param>` balises.</span><span class="sxs-lookup"><span data-stu-id="15c98-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="15c98-114">Le texte de la `<param>` balise s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport Web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="15c98-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="15c98-115">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="15c98-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="15c98-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="15c98-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="15c98-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15c98-117">See also</span></span>

- [<span data-ttu-id="15c98-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="15c98-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="15c98-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="15c98-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
