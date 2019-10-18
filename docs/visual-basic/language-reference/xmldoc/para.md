---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524741"
---
# <a name="para-visual-basic"></a><span data-ttu-id="92825-102">> \<para (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92825-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="92825-103">Spécifie que le contenu est mis en forme en tant que paragraphe.</span><span class="sxs-lookup"><span data-stu-id="92825-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92825-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="92825-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92825-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="92825-106">Texte du paragraphe.</span><span class="sxs-lookup"><span data-stu-id="92825-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92825-107">Notes</span><span class="sxs-lookup"><span data-stu-id="92825-107">Remarks</span></span>  
 <span data-ttu-id="92825-108">La balise `<para>` est destinée à être utilisée à l’intérieur d’une balise, telle que [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) [ou \<returns >,](../../../visual-basic/language-reference/xmldoc/returns.md)et vous permet d’ajouter une structure au texte.</span><span class="sxs-lookup"><span data-stu-id="92825-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="92825-109">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="92825-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92825-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="92825-110">Example</span></span>  
 <span data-ttu-id="92825-111">Cet exemple utilise la balise `<para>` pour fractionner la section Notes de la méthode `UpdateRecord` en deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="92825-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="92825-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92825-112">See also</span></span>

- [<span data-ttu-id="92825-113">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="92825-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
