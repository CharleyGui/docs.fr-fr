---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e3f386d2a1e15ea3e1519d6e1e5e31c34c73fb99
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872900"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="82a42-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82a42-101">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="82a42-102">Spécifie les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="82a42-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a42-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82a42-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="82a42-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82a42-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="82a42-105">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="82a42-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="82a42-106">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="82a42-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="82a42-107">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="82a42-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="82a42-108">Une description.</span><span class="sxs-lookup"><span data-stu-id="82a42-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82a42-109">Notes</span><span class="sxs-lookup"><span data-stu-id="82a42-109">Remarks</span></span>  

 <span data-ttu-id="82a42-110">Utilisez la `<exception>` balise pour spécifier les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="82a42-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="82a42-111">Cette balise est appliquée à une définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="82a42-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="82a42-112">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="82a42-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82a42-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="82a42-113">Example</span></span>  

 <span data-ttu-id="82a42-114">Cet exemple utilise la `<exception>` balise pour décrire une exception que la `IntDivide` fonction peut lever.</span><span class="sxs-lookup"><span data-stu-id="82a42-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="82a42-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82a42-115">See also</span></span>

- [<span data-ttu-id="82a42-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="82a42-116">XML Comment Tags</span></span>](index.md)
