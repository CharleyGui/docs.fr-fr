---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 51eaaef2ddb88afbb52ab58b85ed1a58ba251c1e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866444"
---
# <a name="see-visual-basic"></a><span data-ttu-id="2d12e-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d12e-101">\<see> (Visual Basic)</span></span>

<span data-ttu-id="2d12e-102">Spécifie un lien vers un autre membre.</span><span class="sxs-lookup"><span data-stu-id="2d12e-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d12e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d12e-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d12e-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d12e-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="2d12e-105">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="2d12e-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2d12e-106">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="2d12e-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="2d12e-107">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="2d12e-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d12e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2d12e-108">Remarks</span></span>  

 <span data-ttu-id="2d12e-109">Utilisez la `<see>` balise pour spécifier un lien à partir de texte.</span><span class="sxs-lookup"><span data-stu-id="2d12e-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="2d12e-110">Utilisez [\<seealso>](seealso.md) pour indiquer le texte que vous souhaitez voir apparaître dans une section « Voir aussi ».</span><span class="sxs-lookup"><span data-stu-id="2d12e-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="2d12e-111">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="2d12e-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d12e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d12e-112">Example</span></span>  

 <span data-ttu-id="2d12e-113">Cet exemple utilise la `<see>` balise dans la `UpdateRecord` section Notes pour faire référence à la `DoesRecordExist` méthode.</span><span class="sxs-lookup"><span data-stu-id="2d12e-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2d12e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d12e-114">See also</span></span>

- [<span data-ttu-id="2d12e-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="2d12e-115">XML Comment Tags</span></span>](index.md)
