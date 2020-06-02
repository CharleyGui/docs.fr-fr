---
title: <value> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287192"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="0a547-102">\<value>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0a547-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a547-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a547-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="0a547-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a547-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="0a547-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="0a547-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a547-106">Notes</span><span class="sxs-lookup"><span data-stu-id="0a547-106">Remarks</span></span>

<span data-ttu-id="0a547-107">La `<value>` balise vous permet de décrire la valeur représentée par une propriété.</span><span class="sxs-lookup"><span data-stu-id="0a547-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="0a547-108">Lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio .NET, elle ajoute une [\<summary>](./summary.md) balise pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="0a547-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="0a547-109">Vous devez ensuite ajouter manuellement une `<value>` balise pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="0a547-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="0a547-110">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="0a547-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0a547-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a547-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="0a547-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a547-112">See also</span></span>

- [<span data-ttu-id="0a547-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0a547-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0a547-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="0a547-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
