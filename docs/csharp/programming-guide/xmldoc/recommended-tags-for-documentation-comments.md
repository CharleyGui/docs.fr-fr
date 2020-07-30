---
title: Balises recommandées pour les commentaires de documentation-Guide de programmation C#
description: En savoir plus sur les balises recommandées pour les commentaires de documentation. Consultez la liste des balises recommandées et affichez les ressources disponibles supplémentaires.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 65bca6f979c5ffd91507b571a4f049377315192d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381513"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="1849d-104">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1849d-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="1849d-105">Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**.</span><span class="sxs-lookup"><span data-stu-id="1849d-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="1849d-106">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="1849d-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="1849d-107">Les balises sont traitées sur les constructions de code telles que les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="1849d-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="1849d-108">Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1849d-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="1849d-109">Le compilateur traite toute balise représentant du code XML correct.</span><span class="sxs-lookup"><span data-stu-id="1849d-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="1849d-110">Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1849d-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="1849d-111">Balises</span><span class="sxs-lookup"><span data-stu-id="1849d-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="1849d-112">( \* indique que le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="1849d-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="1849d-113">Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="1849d-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="1849d-114">Cet encodage est illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1849d-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="1849d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1849d-115">See also</span></span>

- [<span data-ttu-id="1849d-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1849d-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1849d-117">-doc (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="1849d-117">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="1849d-118">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="1849d-118">XML documentation comments</span></span>](./index.md)
