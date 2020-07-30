---
title: <value> -Guide de programmation C#
description: En savoir plus sur le XML <value> balise. Cette balise vous permet de décrire la valeur représentée par une propriété.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380772"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="c3868-105">\<value>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c3868-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3868-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3868-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="c3868-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3868-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="c3868-108">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c3868-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3868-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c3868-109">Remarks</span></span>

<span data-ttu-id="c3868-110">La `<value>` balise vous permet de décrire la valeur représentée par une propriété.</span><span class="sxs-lookup"><span data-stu-id="c3868-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="c3868-111">Lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio .NET, elle ajoute une [\<summary>](./summary.md) balise pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="c3868-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="c3868-112">Vous devez ensuite ajouter manuellement une `<value>` balise pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="c3868-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="c3868-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c3868-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c3868-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3868-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="c3868-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3868-115">See also</span></span>

- [<span data-ttu-id="c3868-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c3868-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c3868-117">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c3868-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
