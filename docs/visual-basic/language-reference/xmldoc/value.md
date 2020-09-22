---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875175"
---
# <a name="value-visual-basic"></a><span data-ttu-id="3d32d-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d32d-101">\<value> (Visual Basic)</span></span>

<span data-ttu-id="3d32d-102">Spécifie la description d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="3d32d-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d32d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d32d-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d32d-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d32d-104">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="3d32d-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3d32d-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d32d-106">Notes</span><span class="sxs-lookup"><span data-stu-id="3d32d-106">Remarks</span></span>  

 <span data-ttu-id="3d32d-107">Utilisez la `<value>` balise pour décrire une propriété.</span><span class="sxs-lookup"><span data-stu-id="3d32d-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="3d32d-108">Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio, elle ajoute une [\<summary>](summary.md) balise pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="3d32d-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="3d32d-109">Vous devez ensuite ajouter manuellement une `<value>` balise pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="3d32d-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3d32d-110">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3d32d-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d32d-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d32d-111">Example</span></span>  

 <span data-ttu-id="3d32d-112">Cet exemple utilise la `<value>` balise pour décrire la valeur que la `Counter` propriété contient.</span><span class="sxs-lookup"><span data-stu-id="3d32d-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3d32d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d32d-113">See also</span></span>

- [<span data-ttu-id="3d32d-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="3d32d-114">XML Comment Tags</span></span>](index.md)
