---
title: <seealso> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093459"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="f5cb4-102">\<seealso > (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="f5cb4-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5cb4-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5cb4-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="f5cb4-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5cb4-104">Parameters</span></span>

- <span data-ttu-id="f5cb4-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="f5cb4-105">cref = " `member`"</span></span>

  <span data-ttu-id="f5cb4-106">Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="f5cb4-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f5cb4-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member`</span><span class="sxs-lookup"><span data-stu-id="f5cb4-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="f5cb4-108">doit être placé entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="f5cb4-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="f5cb4-109">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="f5cb4-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="f5cb4-110">Notes</span><span class="sxs-lookup"><span data-stu-id="f5cb4-110">Remarks</span></span>

<span data-ttu-id="f5cb4-111">La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="f5cb4-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="f5cb4-112">Utilisez [\<see>](./see.md) pour spécifier un lien à partir de l’intérieur du texte.</span><span class="sxs-lookup"><span data-stu-id="f5cb4-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="f5cb4-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="f5cb4-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f5cb4-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5cb4-114">Example</span></span>

<span data-ttu-id="f5cb4-115">Pour obtenir un exemple d’utilisation de [seealso>, consultez \<](./summary.md)summary>\<.</span><span class="sxs-lookup"><span data-stu-id="f5cb4-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5cb4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5cb4-116">See also</span></span>

- [<span data-ttu-id="f5cb4-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f5cb4-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f5cb4-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="f5cb4-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
