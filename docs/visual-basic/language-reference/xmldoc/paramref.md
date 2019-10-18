---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 85171bd8deeb5f54c4560bb8b2339107bb8d8c68
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524705"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="0c24a-102">> \<paramref (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c24a-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="0c24a-103">Met en forme un mot en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="0c24a-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c24a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c24a-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c24a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c24a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="0c24a-106">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="0c24a-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="0c24a-107">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="0c24a-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c24a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0c24a-108">Remarks</span></span>  
 <span data-ttu-id="0c24a-109">La balise `<paramref>` vous donne un moyen d’indiquer qu’un mot est un paramètre.</span><span class="sxs-lookup"><span data-stu-id="0c24a-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="0c24a-110">Le fichier XML peut être traité pour mettre en forme ce paramètre de manière distincte.</span><span class="sxs-lookup"><span data-stu-id="0c24a-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="0c24a-111">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="0c24a-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c24a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c24a-112">Example</span></span>  
 <span data-ttu-id="0c24a-113">Cet exemple utilise la balise `<paramref>` pour faire référence au paramètre `id`.</span><span class="sxs-lookup"><span data-stu-id="0c24a-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0c24a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c24a-114">See also</span></span>

- [<span data-ttu-id="0c24a-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="0c24a-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
