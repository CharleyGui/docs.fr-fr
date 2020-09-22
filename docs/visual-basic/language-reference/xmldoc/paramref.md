---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: d7aacc5faea22f9c5a4b865a32c832154fe624c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872616"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="cd509-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd509-101">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="cd509-102">Met en forme un mot en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="cd509-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd509-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd509-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd509-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd509-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="cd509-105">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="cd509-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="cd509-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="cd509-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd509-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cd509-107">Remarks</span></span>  

 <span data-ttu-id="cd509-108">La `<paramref>` balise vous donne un moyen d’indiquer qu’un mot est un paramètre.</span><span class="sxs-lookup"><span data-stu-id="cd509-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="cd509-109">Le fichier XML peut être traité pour mettre en forme ce paramètre de manière distincte.</span><span class="sxs-lookup"><span data-stu-id="cd509-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="cd509-110">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="cd509-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd509-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd509-111">Example</span></span>  

 <span data-ttu-id="cd509-112">Cet exemple utilise la `<paramref>` balise pour faire référence au `id` paramètre.</span><span class="sxs-lookup"><span data-stu-id="cd509-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cd509-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd509-113">See also</span></span>

- [<span data-ttu-id="cd509-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="cd509-114">XML Comment Tags</span></span>](index.md)
