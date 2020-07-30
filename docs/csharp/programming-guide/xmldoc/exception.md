---
title: <exception>-Guide de programmation C#
description: En savoir plus sur la <exception> balise XML. Cette balise vous permet de spécifier les exceptions qui peuvent être levées et qui peuvent être appliquées à des méthodes, des propriétés, des événements et des indexeurs.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381734"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="e3d70-104">\<exception>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e3d70-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3d70-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3d70-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="e3d70-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3d70-106">Parameters</span></span>

- <span data-ttu-id="e3d70-107">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="e3d70-107">cref = " `member`"</span></span>

  <span data-ttu-id="e3d70-108">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="e3d70-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="e3d70-109">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="e3d70-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="e3d70-110">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="e3d70-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="e3d70-111">Pour plus d’informations sur la façon de mettre en forme `member` pour référencer un type générique, consultez [Traitement du fichier XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="e3d70-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="e3d70-112">Description de l'exception.</span><span class="sxs-lookup"><span data-stu-id="e3d70-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3d70-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e3d70-113">Remarks</span></span>

<span data-ttu-id="e3d70-114">La `<exception>` balise vous permet de spécifier les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="e3d70-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="e3d70-115">Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.</span><span class="sxs-lookup"><span data-stu-id="e3d70-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="e3d70-116">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="e3d70-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="e3d70-117">Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3d70-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3d70-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3d70-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="e3d70-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3d70-119">See also</span></span>

- [<span data-ttu-id="e3d70-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e3d70-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e3d70-121">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e3d70-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
