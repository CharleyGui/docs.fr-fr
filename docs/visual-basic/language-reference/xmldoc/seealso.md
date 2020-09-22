---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: f435fa2ab86d81053cd185f5d90ec22996a1458d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869415"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="abdb8-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abdb8-101">\<seealso> (Visual Basic)</span></span>

<span data-ttu-id="abdb8-102">Spécifie un lien qui apparaît dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="abdb8-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdb8-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abdb8-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="abdb8-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="abdb8-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="abdb8-105">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="abdb8-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="abdb8-106">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="abdb8-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="abdb8-107">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="abdb8-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abdb8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="abdb8-108">Remarks</span></span>  

 <span data-ttu-id="abdb8-109">Utilisez la `<seealso>` balise pour spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="abdb8-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="abdb8-110">Utilisez [\<see>](see.md) pour spécifier un lien à partir de texte.</span><span class="sxs-lookup"><span data-stu-id="abdb8-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="abdb8-111">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="abdb8-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abdb8-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="abdb8-112">Example</span></span>  

 <span data-ttu-id="abdb8-113">Cet exemple utilise la `<seealso>` balise dans la `DoesRecordExist` section Notes pour faire référence à la `UpdateRecord` méthode.</span><span class="sxs-lookup"><span data-stu-id="abdb8-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="abdb8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abdb8-114">See also</span></span>

- [<span data-ttu-id="abdb8-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="abdb8-115">XML Comment Tags</span></span>](index.md)
