---
title: <typeparam> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 04145b82cbed0e9a5cae38ff9ef33d061ee792c9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694528"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="bda2e-102">\<typeparam> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bda2e-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="bda2e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bda2e-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda2e-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="bda2e-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bda2e-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="bda2e-105">The name of the type parameter.</span></span> <span data-ttu-id="bda2e-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="bda2e-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="bda2e-107">Description du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="bda2e-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bda2e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bda2e-108">Remarks</span></span>  
 <span data-ttu-id="bda2e-109">La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="bda2e-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="bda2e-110">Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.</span><span class="sxs-lookup"><span data-stu-id="bda2e-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="bda2e-111">Pour plus d’informations, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="bda2e-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="bda2e-112">Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="bda2e-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="bda2e-113">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="bda2e-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bda2e-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="bda2e-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="bda2e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bda2e-115">See also</span></span>

- [<span data-ttu-id="bda2e-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="bda2e-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="bda2e-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bda2e-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bda2e-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="bda2e-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
