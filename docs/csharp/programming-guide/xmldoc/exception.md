---
title: <exception>- Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789804"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="42b70-102">\<> d’exception (guide de programmation de C)</span><span class="sxs-lookup"><span data-stu-id="42b70-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="42b70-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42b70-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="42b70-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42b70-104">Parameters</span></span>

- <span data-ttu-id="42b70-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="42b70-105">cref = " `member`"</span></span>

  <span data-ttu-id="42b70-106">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="42b70-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="42b70-107">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="42b70-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="42b70-108">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="42b70-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="42b70-109">Pour plus d’informations sur la façon de mettre en forme `member` pour référencer un type générique, consultez [Traitement du fichier XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="42b70-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="42b70-110">Description de l'exception.</span><span class="sxs-lookup"><span data-stu-id="42b70-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="42b70-111">Notes </span><span class="sxs-lookup"><span data-stu-id="42b70-111">Remarks</span></span>

<span data-ttu-id="42b70-112">La balise \<exception> vous permet de spécifier quelles exceptions peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="42b70-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="42b70-113">Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.</span><span class="sxs-lookup"><span data-stu-id="42b70-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="42b70-114">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="42b70-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="42b70-115">Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="42b70-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="42b70-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="42b70-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="42b70-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42b70-117">See also</span></span>

- [<span data-ttu-id="42b70-118">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="42b70-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="42b70-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="42b70-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
