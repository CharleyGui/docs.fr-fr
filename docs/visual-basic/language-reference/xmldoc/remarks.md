---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 70078752495240ab8c72fe1bbecdca554166fb22
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866421"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="3bb79-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bb79-101">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="3bb79-102">Spécifie une section Notes pour le membre.</span><span class="sxs-lookup"><span data-stu-id="3bb79-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb79-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bb79-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bb79-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bb79-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="3bb79-105">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="3bb79-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bb79-106">Notes</span><span class="sxs-lookup"><span data-stu-id="3bb79-106">Remarks</span></span>  

 <span data-ttu-id="3bb79-107">Utilisez la `<remarks>` balise pour ajouter des informations sur un type, en complétant les informations spécifiées avec [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="3bb79-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="3bb79-108">Ces informations s’affichent dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="3bb79-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="3bb79-109">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="3bb79-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="3bb79-110">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3bb79-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bb79-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3bb79-111">Example</span></span>  

 <span data-ttu-id="3bb79-112">Cet exemple utilise la `<remarks>` balise pour expliquer ce que `UpdateRecord` fait la méthode.</span><span class="sxs-lookup"><span data-stu-id="3bb79-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3bb79-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bb79-113">See also</span></span>

- [<span data-ttu-id="3bb79-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="3bb79-114">XML Comment Tags</span></span>](index.md)
