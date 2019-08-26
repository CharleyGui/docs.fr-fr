---
title: <param> - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: e2e9bd4478ceaf2f491aba0aa3db8bae7857f28d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587922"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="c5e26-102">\<param> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c5e26-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c5e26-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5e26-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5e26-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5e26-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c5e26-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="c5e26-105">The name of a method parameter.</span></span> <span data-ttu-id="c5e26-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="c5e26-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c5e26-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c5e26-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5e26-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5e26-108">Remarks</span></span>  
 <span data-ttu-id="c5e26-109">La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c5e26-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="c5e26-110">Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param>.</span><span class="sxs-lookup"><span data-stu-id="c5e26-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="c5e26-111">Le texte de la balise \<param> s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="c5e26-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="c5e26-112">Compilez avec [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c5e26-112">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5e26-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="c5e26-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c5e26-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5e26-114">See also</span></span>

- [<span data-ttu-id="c5e26-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c5e26-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c5e26-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c5e26-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
