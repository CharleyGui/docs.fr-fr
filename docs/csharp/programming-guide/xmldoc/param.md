---
title: <param> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287322"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="956ff-102">\<param>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="956ff-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="956ff-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="956ff-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="956ff-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="956ff-104">Parameters</span></span>

- `name`

  <span data-ttu-id="956ff-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="956ff-105">The name of a method parameter.</span></span> <span data-ttu-id="956ff-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="956ff-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="956ff-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="956ff-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="956ff-108">Notes</span><span class="sxs-lookup"><span data-stu-id="956ff-108">Remarks</span></span>

<span data-ttu-id="956ff-109">La `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="956ff-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="956ff-110">Pour documenter plusieurs paramètres, utilisez plusieurs `<param>` balises.</span><span class="sxs-lookup"><span data-stu-id="956ff-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="956ff-111">Le texte de la `<param>` balise s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport Web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="956ff-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="956ff-112">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="956ff-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="956ff-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="956ff-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="956ff-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="956ff-114">See also</span></span>

- [<span data-ttu-id="956ff-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="956ff-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="956ff-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="956ff-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
