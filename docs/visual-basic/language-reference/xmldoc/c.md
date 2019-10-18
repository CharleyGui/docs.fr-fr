---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523944"
---
# <a name="c-visual-basic"></a><span data-ttu-id="a14e9-102">> \<c (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a14e9-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="a14e9-103">Indique que le texte d’une description est du code.</span><span class="sxs-lookup"><span data-stu-id="a14e9-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a14e9-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a14e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a14e9-105">Parameters</span></span>  
  
|<span data-ttu-id="a14e9-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a14e9-106">Parameter</span></span>|<span data-ttu-id="a14e9-107">Description</span><span class="sxs-lookup"><span data-stu-id="a14e9-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="a14e9-108">Texte que vous souhaitez indiquer comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="a14e9-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a14e9-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a14e9-109">Remarks</span></span>  
 <span data-ttu-id="a14e9-110">La balise `<c>` vous donne un moyen d’indiquer que le texte d’une description doit être marqué comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="a14e9-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="a14e9-111">Utilisez [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) pour indiquer plusieurs lignes comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="a14e9-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="a14e9-112">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="a14e9-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a14e9-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a14e9-113">Example</span></span>  
 <span data-ttu-id="a14e9-114">Cet exemple utilise la balise `<c>` dans la section Summary pour indiquer que `Counter` est du code.</span><span class="sxs-lookup"><span data-stu-id="a14e9-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a14e9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a14e9-115">See also</span></span>

- [<span data-ttu-id="a14e9-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="a14e9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
