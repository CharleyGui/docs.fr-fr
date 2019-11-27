---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352240"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="4f5e3-101">\<retourne > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f5e3-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="4f5e3-102">Spécifie la valeur de retour de la propriété ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="4f5e3-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5e3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f5e3-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f5e3-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f5e3-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4f5e3-105">Description de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="4f5e3-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f5e3-106">Notes</span><span class="sxs-lookup"><span data-stu-id="4f5e3-106">Remarks</span></span>  
 <span data-ttu-id="4f5e3-107">Utilisez la balise `<returns>` dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="4f5e3-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="4f5e3-108">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="4f5e3-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f5e3-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f5e3-109">Example</span></span>  
 <span data-ttu-id="4f5e3-110">Cet exemple utilise la balise `<returns>` pour expliquer ce que la fonction `DoesRecordExist` retourne.</span><span class="sxs-lookup"><span data-stu-id="4f5e3-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4f5e3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f5e3-111">See also</span></span>

- [<span data-ttu-id="4f5e3-112">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="4f5e3-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
