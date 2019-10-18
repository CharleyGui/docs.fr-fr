---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 25a0b307756401bed4d4c77d3668c2af53ba8b42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524634"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="d747c-102">> \<summary (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d747c-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="d747c-103">Spécifie le résumé du membre.</span><span class="sxs-lookup"><span data-stu-id="d747c-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d747c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d747c-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d747c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d747c-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="d747c-106">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d747c-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d747c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d747c-107">Remarks</span></span>  
 <span data-ttu-id="d747c-108">Utilisez la balise `<summary>` pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="d747c-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="d747c-109">Utilisez [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="d747c-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="d747c-110">Le texte de la balise `<summary>` est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="d747c-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="d747c-111">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="d747c-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="d747c-112">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="d747c-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d747c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d747c-113">Example</span></span>  
 <span data-ttu-id="d747c-114">Cet exemple utilise la balise `<summary>` pour décrire la méthode `ResetCounter` et la propriété `Counter`.</span><span class="sxs-lookup"><span data-stu-id="d747c-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d747c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d747c-115">See also</span></span>

- [<span data-ttu-id="d747c-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="d747c-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
