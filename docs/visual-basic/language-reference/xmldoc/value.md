---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352171"
---
# <a name="value-visual-basic"></a><span data-ttu-id="05083-101">> de la valeur \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05083-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="05083-102">Spécifie la description d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="05083-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05083-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05083-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="05083-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05083-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="05083-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="05083-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05083-106">Notes</span><span class="sxs-lookup"><span data-stu-id="05083-106">Remarks</span></span>  
 <span data-ttu-id="05083-107">Utilisez la balise `<value>` pour décrire une propriété.</span><span class="sxs-lookup"><span data-stu-id="05083-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="05083-108">Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio, elle ajoute une balise de [>\<Summary](../../../visual-basic/language-reference/xmldoc/summary.md) pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="05083-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="05083-109">Vous devez ensuite ajouter manuellement une balise `<value>` pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="05083-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="05083-110">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="05083-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05083-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="05083-111">Example</span></span>  
 <span data-ttu-id="05083-112">Cet exemple utilise la balise `<value>` pour décrire la valeur que la propriété `Counter` contient.</span><span class="sxs-lookup"><span data-stu-id="05083-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="05083-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05083-113">See also</span></span>

- [<span data-ttu-id="05083-114">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="05083-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
