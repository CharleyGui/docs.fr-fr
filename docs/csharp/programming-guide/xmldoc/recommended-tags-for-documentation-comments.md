---
title: Balises recommandées pour les commentaires de documentation - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 07594d70b92e2075c3d5aba605eab23d766faed6
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052749"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="1f242-102">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1f242-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="1f242-103">Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**.</span><span class="sxs-lookup"><span data-stu-id="1f242-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="1f242-104">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="1f242-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="1f242-105">Les balises sont traitées sur les constructions de code telles que les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="1f242-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f242-106">Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f242-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="1f242-107">Le compilateur traite toute balise représentant du code XML correct.</span><span class="sxs-lookup"><span data-stu-id="1f242-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="1f242-108">Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1f242-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="1f242-109">Balises</span><span class="sxs-lookup"><span data-stu-id="1f242-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="1f242-110">\<c></span><span class="sxs-lookup"><span data-stu-id="1f242-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="1f242-111">\<para></span><span class="sxs-lookup"><span data-stu-id="1f242-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="1f242-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="1f242-113">\<code></span><span class="sxs-lookup"><span data-stu-id="1f242-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="1f242-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="1f242-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="1f242-116">\<example></span><span class="sxs-lookup"><span data-stu-id="1f242-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="1f242-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="1f242-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="1f242-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="1f242-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="1f242-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="1f242-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="1f242-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="1f242-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="1f242-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="1f242-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="1f242-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="1f242-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="1f242-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="1f242-125">\<list></span><span class="sxs-lookup"><span data-stu-id="1f242-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="1f242-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="1f242-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="1f242-127">\<value></span><span class="sxs-lookup"><span data-stu-id="1f242-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="1f242-128">(\* indique que le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="1f242-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="1f242-129">Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="1f242-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="1f242-130">Ce codage est illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1f242-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="1f242-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f242-131">See also</span></span>

- [<span data-ttu-id="1f242-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1f242-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1f242-133">/doc (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="1f242-133">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="1f242-134">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="1f242-134">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/index.md)
