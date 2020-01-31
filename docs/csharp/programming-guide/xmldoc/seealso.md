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
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789681"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="3a6d2-102">\<seealso > (C# Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="3a6d2-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a6d2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a6d2-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="3a6d2-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="3a6d2-104">Parameters</span></span>

- <span data-ttu-id="3a6d2-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="3a6d2-105">cref = " `member`"</span></span>

  <span data-ttu-id="3a6d2-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="3a6d2-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member`</span><span class="sxs-lookup"><span data-stu-id="3a6d2-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="3a6d2-108">doit être placé entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="3a6d2-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="3a6d2-109">Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="3a6d2-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="3a6d2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3a6d2-110">Remarks</span></span>

<span data-ttu-id="3a6d2-111">La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="3a6d2-112">Utilisez [\<see>](./see.md) pour spécifier un lien à partir de l’intérieur du texte.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="3a6d2-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="3a6d2-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a6d2-114">Example</span></span>

<span data-ttu-id="3a6d2-115">Pour obtenir un exemple d’utilisation de \<seealso>, consultez [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="3a6d2-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a6d2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a6d2-116">See also</span></span>

- [<span data-ttu-id="3a6d2-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3a6d2-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="3a6d2-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="3a6d2-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
