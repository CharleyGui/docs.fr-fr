---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 380923c2313450afc5745b25eeea6a444705dd3f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411523"
---
# <a name="see-visual-basic"></a><span data-ttu-id="5ced2-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ced2-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="5ced2-102">Spécifie un lien vers un autre membre.</span><span class="sxs-lookup"><span data-stu-id="5ced2-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ced2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ced2-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ced2-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ced2-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="5ced2-105">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="5ced2-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="5ced2-106">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="5ced2-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="5ced2-107">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="5ced2-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ced2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5ced2-108">Remarks</span></span>  
 <span data-ttu-id="5ced2-109">Utilisez la `<see>` balise pour spécifier un lien à partir de texte.</span><span class="sxs-lookup"><span data-stu-id="5ced2-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="5ced2-110">Utilisez [\<seealso>](seealso.md) pour indiquer le texte que vous souhaitez voir apparaître dans une section « Voir aussi ».</span><span class="sxs-lookup"><span data-stu-id="5ced2-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="5ced2-111">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="5ced2-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ced2-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="5ced2-112">Example</span></span>  
 <span data-ttu-id="5ced2-113">Cet exemple utilise la `<see>` balise dans la `UpdateRecord` section Notes pour faire référence à la `DoesRecordExist` méthode.</span><span class="sxs-lookup"><span data-stu-id="5ced2-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5ced2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ced2-114">See also</span></span>

- [<span data-ttu-id="5ced2-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="5ced2-115">XML Comment Tags</span></span>](index.md)
