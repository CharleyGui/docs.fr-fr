---
title: <seealso> -Guide de programmation C#
description: Découvrez comment utiliser le XML <seealso> balise. Cette balise vous permet de spécifier le texte que vous souhaitez voir apparaître dans la section « Voir aussi ».
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
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380642"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="1d110-105">\<seealso>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1d110-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d110-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d110-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="1d110-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d110-107">Parameters</span></span>

- <span data-ttu-id="1d110-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="1d110-108">cref = " `member`"</span></span>

  <span data-ttu-id="1d110-109">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="1d110-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1d110-110">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member`</span><span class="sxs-lookup"><span data-stu-id="1d110-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="1d110-111">doit être placé entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="1d110-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="1d110-112">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="1d110-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="1d110-113">Notes</span><span class="sxs-lookup"><span data-stu-id="1d110-113">Remarks</span></span>

<span data-ttu-id="1d110-114">La `<seealso>` balise vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="1d110-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="1d110-115">Utilisez [\<see>](./see.md) pour spécifier un lien à partir de texte.</span><span class="sxs-lookup"><span data-stu-id="1d110-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="1d110-116">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="1d110-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1d110-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d110-117">Example</span></span>

<span data-ttu-id="1d110-118">[\<summary>](./summary.md)Pour obtenir un exemple d’utilisation de \<seealso> , consultez.</span><span class="sxs-lookup"><span data-stu-id="1d110-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d110-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d110-119">See also</span></span>

- [<span data-ttu-id="1d110-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1d110-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1d110-121">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="1d110-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
