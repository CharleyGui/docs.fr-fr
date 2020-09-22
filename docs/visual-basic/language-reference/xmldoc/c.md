---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871705"
---
# <a name="c-visual-basic"></a><span data-ttu-id="aec22-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec22-101">\<c> (Visual Basic)</span></span>

<span data-ttu-id="aec22-102">Indique que le texte d’une description est du code.</span><span class="sxs-lookup"><span data-stu-id="aec22-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aec22-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aec22-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="aec22-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aec22-104">Parameters</span></span>  
  
|<span data-ttu-id="aec22-105">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aec22-105">Parameter</span></span>|<span data-ttu-id="aec22-106">Description</span><span class="sxs-lookup"><span data-stu-id="aec22-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="aec22-107">Texte que vous souhaitez indiquer comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="aec22-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aec22-108">Notes</span><span class="sxs-lookup"><span data-stu-id="aec22-108">Remarks</span></span>  

 <span data-ttu-id="aec22-109">La `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="aec22-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="aec22-110">Utilisez [\<code>](code.md) pour indiquer plusieurs lignes en tant que code.</span><span class="sxs-lookup"><span data-stu-id="aec22-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="aec22-111">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="aec22-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aec22-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="aec22-112">Example</span></span>  

 <span data-ttu-id="aec22-113">Cet exemple utilise la `<c>` balise dans la section Summary pour indiquer que `Counter` est du code.</span><span class="sxs-lookup"><span data-stu-id="aec22-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aec22-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aec22-114">See also</span></span>

- [<span data-ttu-id="aec22-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="aec22-115">XML Comment Tags</span></span>](index.md)
