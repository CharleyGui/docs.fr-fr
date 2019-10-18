---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523920"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="3b748-102">> \<exception (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b748-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="3b748-103">Spécifie les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="3b748-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b748-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b748-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b748-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b748-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="3b748-106">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="3b748-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="3b748-107">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="3b748-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="3b748-108">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="3b748-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3b748-109">Description.</span><span class="sxs-lookup"><span data-stu-id="3b748-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b748-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3b748-110">Remarks</span></span>  
 <span data-ttu-id="3b748-111">Utilisez la balise `<exception>` pour spécifier les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="3b748-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="3b748-112">Cette balise est appliquée à une définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="3b748-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="3b748-113">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3b748-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b748-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b748-114">Example</span></span>  
 <span data-ttu-id="3b748-115">Cet exemple utilise la balise `<exception>` pour décrire une exception que la fonction `IntDivide` peut lever.</span><span class="sxs-lookup"><span data-stu-id="3b748-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3b748-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b748-116">See also</span></span>

- [<span data-ttu-id="3b748-117">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="3b748-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
