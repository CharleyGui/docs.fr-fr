---
title: <see>-Guide de programmation C#
description: En savoir plus sur la <see> balise XML. Cette balise vous permet de spécifier un lien à partir du texte, par exemple à l’aide d’un attribut cref.
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
ms.openlocfilehash: 1cc4982d1ebe9d6896404218a6d200b10cc6503f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381929"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="153aa-104">\<see>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="153aa-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="153aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="153aa-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="153aa-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="153aa-106">Parameters</span></span>

- <span data-ttu-id="153aa-107">CREF = " `member` "</span><span class="sxs-lookup"><span data-stu-id="153aa-107">cref = "`member`"</span></span>

  <span data-ttu-id="153aa-108">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="153aa-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="153aa-109">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="153aa-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="153aa-110">Placez le *membre* entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="153aa-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="153aa-111">Notes</span><span class="sxs-lookup"><span data-stu-id="153aa-111">Remarks</span></span>

<span data-ttu-id="153aa-112">La `<see>` balise vous permet de spécifier un lien à partir de texte.</span><span class="sxs-lookup"><span data-stu-id="153aa-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="153aa-113">Utilisez [\<seealso>](./seealso.md) pour indiquer que le texte doit être placé dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="153aa-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="153aa-114">Utilisez l’[attribut cref](./cref-attribute.md) pour créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="153aa-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="153aa-115">En outre, ``href`` est un attribut valide qui fonctionnera comme un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="153aa-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="153aa-116">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="153aa-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="153aa-117">L’exemple suivant montre une `<see>` balise dans une section Résumé.</span><span class="sxs-lookup"><span data-stu-id="153aa-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="153aa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="153aa-118">See also</span></span>

- [<span data-ttu-id="153aa-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="153aa-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="153aa-120">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="153aa-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
