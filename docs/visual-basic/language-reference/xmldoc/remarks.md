---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400019"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="9b375-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b375-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="9b375-102">Spécifie une section Notes pour le membre.</span><span class="sxs-lookup"><span data-stu-id="9b375-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b375-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b375-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b375-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b375-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="9b375-105">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="9b375-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b375-106">Notes</span><span class="sxs-lookup"><span data-stu-id="9b375-106">Remarks</span></span>  
 <span data-ttu-id="9b375-107">Utilisez la `<remarks>` balise pour ajouter des informations sur un type, en complétant les informations spécifiées avec [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="9b375-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="9b375-108">Ces informations s’affichent dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="9b375-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="9b375-109">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="9b375-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="9b375-110">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="9b375-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b375-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b375-111">Example</span></span>  
 <span data-ttu-id="9b375-112">Cet exemple utilise la `<remarks>` balise pour expliquer ce que `UpdateRecord` fait la méthode.</span><span class="sxs-lookup"><span data-stu-id="9b375-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9b375-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b375-113">See also</span></span>

- [<span data-ttu-id="9b375-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="9b375-114">XML Comment Tags</span></span>](index.md)
