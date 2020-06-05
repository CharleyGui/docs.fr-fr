---
title: Balises XML recommandées pour les commentaires de documentation
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400097"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="bfbdf-102">Balises XML recommandées pour les commentaires de documentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfbdf-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="bfbdf-103">Le compilateur Visual Basic peut traiter les commentaires de documentation dans votre code dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="bfbdf-104">Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="bfbdf-105">Les commentaires XML sont autorisés sur les constructions de code telles que les types et les membres de type.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="bfbdf-106">Pour les types partiels, une seule partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur les commentaires de ses membres.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfbdf-107">Les commentaires de documentation ne peuvent pas être appliqués aux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="bfbdf-108">La raison en est qu’un espace de noms peut couvrir plusieurs assemblys, et que tous les assemblys ne doivent pas être chargés en même temps.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="bfbdf-109">Le compilateur traite toute balise qui est du code XML valide.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="bfbdf-110">Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bfbdf-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="bfbdf-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="bfbdf-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="bfbdf-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="bfbdf-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="bfbdf-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="bfbdf-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="bfbdf-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bfbdf-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="bfbdf-118">(<sup>1</sup> le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="bfbdf-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfbdf-119">Si vous souhaitez que les chevrons apparaissent dans le texte d’un commentaire de documentation, utilisez `&lt;` et `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="bfbdf-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="bfbdf-120">Par exemple, la chaîne `"&lt;text in angle brackets&gt;"` s’affiche comme `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="bfbdf-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbdf-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfbdf-121">See also</span></span>

- [<span data-ttu-id="bfbdf-122">Documentation de votre code avec le langage XML</span><span class="sxs-lookup"><span data-stu-id="bfbdf-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="bfbdf-123">-doc</span><span class="sxs-lookup"><span data-stu-id="bfbdf-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="bfbdf-124">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="bfbdf-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
