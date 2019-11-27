---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 78227a17584271f91283198e95f5aa389b3ef14b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352277"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="b13d9-101">\<> paramref (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b13d9-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="b13d9-102">Met en forme un mot en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="b13d9-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b13d9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b13d9-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b13d9-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b13d9-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b13d9-105">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="b13d9-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="b13d9-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="b13d9-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b13d9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="b13d9-107">Remarks</span></span>  
 <span data-ttu-id="b13d9-108">La balise `<paramref>` vous donne un moyen d’indiquer qu’un mot est un paramètre.</span><span class="sxs-lookup"><span data-stu-id="b13d9-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="b13d9-109">Le fichier XML peut être traité pour mettre en forme ce paramètre de manière distincte.</span><span class="sxs-lookup"><span data-stu-id="b13d9-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="b13d9-110">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="b13d9-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b13d9-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b13d9-111">Example</span></span>  
 <span data-ttu-id="b13d9-112">Cet exemple utilise la balise `<paramref>` pour faire référence au paramètre `id`.</span><span class="sxs-lookup"><span data-stu-id="b13d9-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b13d9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b13d9-113">See also</span></span>

- [<span data-ttu-id="b13d9-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="b13d9-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
