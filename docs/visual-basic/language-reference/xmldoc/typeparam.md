---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411484"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="55424-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55424-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="55424-102">Définit un nom de paramètre de type et une description.</span><span class="sxs-lookup"><span data-stu-id="55424-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55424-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55424-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="55424-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55424-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="55424-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="55424-105">The name of the type parameter.</span></span> <span data-ttu-id="55424-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="55424-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="55424-107">Description du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="55424-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55424-108">Notes</span><span class="sxs-lookup"><span data-stu-id="55424-108">Remarks</span></span>  
 <span data-ttu-id="55424-109">Utilisez la `<typeparam>` balise dans le commentaire pour un type générique ou une déclaration de membre générique pour décrire l’un des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="55424-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="55424-110">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="55424-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55424-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="55424-111">Example</span></span>  
 <span data-ttu-id="55424-112">Cet exemple utilise la `<typeparam>` balise pour décrire le `id` paramètre.</span><span class="sxs-lookup"><span data-stu-id="55424-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="55424-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55424-113">See also</span></span>

- [<span data-ttu-id="55424-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="55424-114">XML Comment Tags</span></span>](index.md)
