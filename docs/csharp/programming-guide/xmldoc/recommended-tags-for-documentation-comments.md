---
title: Étiquettes recommandées pour les commentaires de documentation - Guide de programmation C
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789726"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="d469b-102">Étiquettes recommandées pour les commentaires de documentation (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="d469b-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="d469b-103">Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**.</span><span class="sxs-lookup"><span data-stu-id="d469b-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="d469b-104">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé, ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="d469b-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="d469b-105">Les balises sont traitées sur les constructions de code telles que les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="d469b-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="d469b-106">Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d469b-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="d469b-107">Le compilateur traite toute balise représentant du code XML correct.</span><span class="sxs-lookup"><span data-stu-id="d469b-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="d469b-108">Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d469b-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="d469b-109">Balises</span><span class="sxs-lookup"><span data-stu-id="d469b-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="d469b-110">\<c></span><span class="sxs-lookup"><span data-stu-id="d469b-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="d469b-111">\<para></span><span class="sxs-lookup"><span data-stu-id="d469b-111">\<para></span></span>](./para.md)|<span data-ttu-id="d469b-112">[\<voir>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="d469b-113">\<>de valeur</span><span class="sxs-lookup"><span data-stu-id="d469b-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="d469b-114">\<>de code</span><span class="sxs-lookup"><span data-stu-id="d469b-114">\<code></span></span>](./code.md)|<span data-ttu-id="d469b-115">[\<>de param](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="d469b-116">[\<>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="d469b-117">\<exemple></span><span class="sxs-lookup"><span data-stu-id="d469b-117">\<example></span></span>](./example.md)|[<span data-ttu-id="d469b-118">\<>paramref</span><span class="sxs-lookup"><span data-stu-id="d469b-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="d469b-119">\<>résumé</span><span class="sxs-lookup"><span data-stu-id="d469b-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="d469b-120">[\<>d’exception](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="d469b-121">[\<autorisation>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="d469b-122">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="d469b-123">[\<inclure>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="d469b-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="d469b-124">\<remarques></span><span class="sxs-lookup"><span data-stu-id="d469b-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="d469b-125">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="d469b-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="d469b-126">\<liste></span><span class="sxs-lookup"><span data-stu-id="d469b-126">\<list></span></span>](./list.md)|[<span data-ttu-id="d469b-127">\<>héritière</span><span class="sxs-lookup"><span data-stu-id="d469b-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="d469b-128">\<retourne></span><span class="sxs-lookup"><span data-stu-id="d469b-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="d469b-129">(\* dénote que le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="d469b-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="d469b-130">Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="d469b-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="d469b-131">Ce codage est indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d469b-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="d469b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d469b-132">See also</span></span>

- [<span data-ttu-id="d469b-133">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="d469b-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d469b-134">-doc (options de compilateur de C)</span><span class="sxs-lookup"><span data-stu-id="d469b-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="d469b-135">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="d469b-135">XML documentation comments</span></span>](./index.md)
