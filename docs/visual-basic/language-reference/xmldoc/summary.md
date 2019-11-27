---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352203"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="0144f-101">> de résumé de la \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0144f-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="0144f-102">Spécifie le résumé du membre.</span><span class="sxs-lookup"><span data-stu-id="0144f-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0144f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0144f-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0144f-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0144f-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0144f-105">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0144f-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0144f-106">Notes</span><span class="sxs-lookup"><span data-stu-id="0144f-106">Remarks</span></span>  
 <span data-ttu-id="0144f-107">Utilisez la balise `<summary>` pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="0144f-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="0144f-108">Utilisez [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="0144f-108">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="0144f-109">Le texte de la balise `<summary>` est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="0144f-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="0144f-110">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="0144f-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="0144f-111">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="0144f-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0144f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="0144f-112">Example</span></span>  
 <span data-ttu-id="0144f-113">Cet exemple utilise la balise `<summary>` pour décrire la méthode `ResetCounter` et la propriété `Counter`.</span><span class="sxs-lookup"><span data-stu-id="0144f-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0144f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0144f-114">See also</span></span>

- [<span data-ttu-id="0144f-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="0144f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
