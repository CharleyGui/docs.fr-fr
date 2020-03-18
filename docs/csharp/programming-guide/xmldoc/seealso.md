---
title: <seealso> - Guide de programmation C
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093459"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="9c357-102">\<seealso> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="9c357-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c357-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c357-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="9c357-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c357-104">Parameters</span></span>

- <span data-ttu-id="9c357-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9c357-105">cref = " `member`"</span></span>

  <span data-ttu-id="9c357-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="9c357-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9c357-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member`</span><span class="sxs-lookup"><span data-stu-id="9c357-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="9c357-108">doit être placé entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="9c357-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="9c357-109">Pour plus d’informations sur la façon de créer une référence de cref à un type générique, voir [attribut de cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="9c357-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="9c357-110">Notes </span><span class="sxs-lookup"><span data-stu-id="9c357-110">Remarks</span></span>

<span data-ttu-id="9c357-111">La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="9c357-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="9c357-112">Utilisez [ \<voir>](./see.md) pour spécifier un lien à partir du texte.</span><span class="sxs-lookup"><span data-stu-id="9c357-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="9c357-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="9c357-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9c357-114"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9c357-114">Example</span></span>

<span data-ttu-id="9c357-115">Voir [ \<le résumé>](./summary.md) par exemple \<d’utilisation de> seealso.</span><span class="sxs-lookup"><span data-stu-id="9c357-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c357-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c357-116">See also</span></span>

- [<span data-ttu-id="9c357-117">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="9c357-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9c357-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="9c357-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
