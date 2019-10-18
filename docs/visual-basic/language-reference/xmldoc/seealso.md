---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0231ff748949874f4b477cac15d891d313b25f4f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524642"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="ceaa2-102">> \<seealso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceaa2-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="ceaa2-103">Spécifie un lien qui apparaît dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceaa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceaa2-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceaa2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ceaa2-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ceaa2-106">Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ceaa2-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="ceaa2-108">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="ceaa2-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceaa2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ceaa2-109">Remarks</span></span>  
 <span data-ttu-id="ceaa2-110">Utilisez la balise `<seealso>` pour spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="ceaa2-111">Utilisez [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) pour spécifier un lien à partir de l’intérieur du texte.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="ceaa2-112">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceaa2-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="ceaa2-113">Example</span></span>  
 <span data-ttu-id="ceaa2-114">Cet exemple utilise la balise `<seealso>` dans la section Notes de `DoesRecordExist` pour faire référence à la méthode `UpdateRecord`.</span><span class="sxs-lookup"><span data-stu-id="ceaa2-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ceaa2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ceaa2-115">See also</span></span>

- [<span data-ttu-id="ceaa2-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="ceaa2-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
