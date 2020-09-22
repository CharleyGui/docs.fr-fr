---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872972"
---
# <a name="example-visual-basic"></a><span data-ttu-id="8f0d7-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f0d7-101">\<example> (Visual Basic)</span></span>

<span data-ttu-id="8f0d7-102">Spécifie un exemple pour le membre.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0d7-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f0d7-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f0d7-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f0d7-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="8f0d7-105">Description de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f0d7-106">Notes</span><span class="sxs-lookup"><span data-stu-id="8f0d7-106">Remarks</span></span>  

 <span data-ttu-id="8f0d7-107">La `<example>` balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="8f0d7-108">Cela implique généralement l’utilisation de la [\<code>](code.md) balise.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="8f0d7-109">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f0d7-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f0d7-110">Example</span></span>  

 <span data-ttu-id="8f0d7-111">Cet exemple utilise la `<example>` balise pour inclure un exemple d’utilisation du `ID` champ.</span><span class="sxs-lookup"><span data-stu-id="8f0d7-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8f0d7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f0d7-112">See also</span></span>

- [<span data-ttu-id="8f0d7-113">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="8f0d7-113">XML Comment Tags</span></span>](index.md)
