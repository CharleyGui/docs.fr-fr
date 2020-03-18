---
title: <see>- Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627670"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="31d11-102">\<voir> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="31d11-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="31d11-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31d11-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="31d11-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31d11-104">Parameters</span></span>

- <span data-ttu-id="31d11-105">cref -`member`"</span><span class="sxs-lookup"><span data-stu-id="31d11-105">cref = "`member`"</span></span>

  <span data-ttu-id="31d11-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="31d11-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="31d11-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="31d11-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="31d11-108">Placez le *membre* entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="31d11-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="31d11-109">Notes </span><span class="sxs-lookup"><span data-stu-id="31d11-109">Remarks</span></span>

<span data-ttu-id="31d11-110">La balise \<see> vous permet de spécifier un lien à partir de l’intérieur du texte.</span><span class="sxs-lookup"><span data-stu-id="31d11-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="31d11-111">Utilisez [ \<seealso>](./seealso.md) pour indiquer que le texte doit être placé dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="31d11-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="31d11-112">Utilisez l’[attribut cref](./cref-attribute.md) pour créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="31d11-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="31d11-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="31d11-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="31d11-114">L’exemple suivant présente une balise \<see> dans une section de résumé (summary).</span><span class="sxs-lookup"><span data-stu-id="31d11-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="31d11-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d11-115">See also</span></span>

- [<span data-ttu-id="31d11-116">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="31d11-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="31d11-117">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="31d11-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
