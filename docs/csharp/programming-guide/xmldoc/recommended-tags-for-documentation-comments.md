---
title: Balises recommandées pour les commentaires de documentation - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 15a183d72a7d3e47f99227cea2cf870ad2f98d18
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696530"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="9fde3-102">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9fde3-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="9fde3-103">Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**.</span><span class="sxs-lookup"><span data-stu-id="9fde3-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="9fde3-104">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="9fde3-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="9fde3-105">Les balises sont traitées sur les constructions de code telles que les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="9fde3-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fde3-106">Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9fde3-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="9fde3-107">Le compilateur traite toute balise représentant du code XML correct.</span><span class="sxs-lookup"><span data-stu-id="9fde3-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="9fde3-108">Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fde3-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="9fde3-109">Balises</span><span class="sxs-lookup"><span data-stu-id="9fde3-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="9fde3-110">\<c></span><span class="sxs-lookup"><span data-stu-id="9fde3-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="9fde3-111">\<para></span><span class="sxs-lookup"><span data-stu-id="9fde3-111">\<para></span></span>](./para.md)|<span data-ttu-id="9fde3-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="9fde3-113">\<code></span><span class="sxs-lookup"><span data-stu-id="9fde3-113">\<code></span></span>](./code.md)|<span data-ttu-id="9fde3-114">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="9fde3-115">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="9fde3-116">\<example></span><span class="sxs-lookup"><span data-stu-id="9fde3-116">\<example></span></span>](./example.md)|[<span data-ttu-id="9fde3-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="9fde3-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="9fde3-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="9fde3-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="9fde3-119">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="9fde3-120">[\<permission>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="9fde3-121">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="9fde3-122">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="9fde3-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="9fde3-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="9fde3-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="9fde3-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="9fde3-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="9fde3-125">\<list></span><span class="sxs-lookup"><span data-stu-id="9fde3-125">\<list></span></span>](./list.md)|[<span data-ttu-id="9fde3-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="9fde3-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="9fde3-127">\<value></span><span class="sxs-lookup"><span data-stu-id="9fde3-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="9fde3-128">(\* indique que le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="9fde3-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="9fde3-129">Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="9fde3-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="9fde3-130">Ce codage est illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9fde3-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="9fde3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fde3-131">See also</span></span>

- [<span data-ttu-id="9fde3-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9fde3-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9fde3-133">-doc (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="9fde3-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="9fde3-134">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="9fde3-134">XML Documentation Comments</span></span>](./index.md)
