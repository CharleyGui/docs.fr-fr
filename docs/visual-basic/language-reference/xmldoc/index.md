---
title: Balises XML recommandées pour les commentaires de documentation (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913504"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="3f5f9-102">Balises XML recommandées pour les commentaires de documentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f5f9-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="3f5f9-103">Le compilateur Visual Basic peut traiter les commentaires de documentation dans votre code dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="3f5f9-104">Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="3f5f9-105">Les commentaires XML sont autorisés sur les constructions de code telles que les types et les membres de type.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="3f5f9-106">Pour les types partiels, une seule partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur les commentaires de ses membres.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f5f9-107">Les commentaires de documentation ne peuvent pas être appliqués aux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="3f5f9-108">La raison en est qu’un espace de noms peut couvrir plusieurs assemblys, et que tous les assemblys ne doivent pas être chargés en même temps.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="3f5f9-109">Le compilateur traite toute balise qui est du code XML valide.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="3f5f9-110">Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="3f5f9-111">\<c></span><span class="sxs-lookup"><span data-stu-id="3f5f9-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="3f5f9-112">\<code></span><span class="sxs-lookup"><span data-stu-id="3f5f9-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="3f5f9-113">\<example></span><span class="sxs-lookup"><span data-stu-id="3f5f9-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="3f5f9-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="3f5f9-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="3f5f9-116">\<list></span><span class="sxs-lookup"><span data-stu-id="3f5f9-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="3f5f9-117">\<para></span><span class="sxs-lookup"><span data-stu-id="3f5f9-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="3f5f9-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="3f5f9-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="3f5f9-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="3f5f9-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="3f5f9-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="3f5f9-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="3f5f9-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="3f5f9-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="3f5f9-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="3f5f9-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="3f5f9-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="3f5f9-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="3f5f9-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f5f9-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="3f5f9-127">\<value></span><span class="sxs-lookup"><span data-stu-id="3f5f9-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="3f5f9-128">(<sup>1</sup> le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="3f5f9-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f5f9-129">Si vous souhaitez que les chevrons apparaissent dans le texte d’un commentaire de documentation `&lt;` , `&gt;`utilisez et.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="3f5f9-130">Par exemple, la chaîne `"&lt;text in angle brackets&gt;"` s’affiche comme `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="3f5f9-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5f9-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f5f9-131">See also</span></span>

- [<span data-ttu-id="3f5f9-132">Documentation de votre code avec le langage XML</span><span class="sxs-lookup"><span data-stu-id="3f5f9-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="3f5f9-133">/doc</span><span class="sxs-lookup"><span data-stu-id="3f5f9-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="3f5f9-134">Guide pratique pour Créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="3f5f9-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
