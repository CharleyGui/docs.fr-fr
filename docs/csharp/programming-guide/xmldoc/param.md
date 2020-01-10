---
title: <param> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711725"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="12258-102">\<param> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="12258-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="12258-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12258-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="12258-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="12258-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="12258-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="12258-105">The name of a method parameter.</span></span> <span data-ttu-id="12258-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="12258-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="12258-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="12258-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12258-108">Notes</span><span class="sxs-lookup"><span data-stu-id="12258-108">Remarks</span></span>  
 <span data-ttu-id="12258-109">La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="12258-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="12258-110">Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param>.</span><span class="sxs-lookup"><span data-stu-id="12258-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="12258-111">Le texte de la balise \<param> s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="12258-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="12258-112">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="12258-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12258-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="12258-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="12258-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12258-114">See also</span></span>

- [<span data-ttu-id="12258-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="12258-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="12258-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="12258-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
