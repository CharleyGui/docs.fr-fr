---
title: <value> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: a30435c40ad31e026b9cb1952086984548f0cdb6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694541"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="af833-102">\<value> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="af833-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="af833-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af833-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="af833-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="af833-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="af833-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="af833-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af833-106">Notes</span><span class="sxs-lookup"><span data-stu-id="af833-106">Remarks</span></span>  
 <span data-ttu-id="af833-107">La balise \<value> vous permet de décrire la valeur représentée par une propriété.</span><span class="sxs-lookup"><span data-stu-id="af833-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="af833-108">Notez que lorsque vous ajoutez une propriété via l’Assistant Code de l’environnement de développement Visual Studio .NET, il ajoute une balise [\<summary>](./summary.md) pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="af833-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="af833-109">Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="af833-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="af833-110">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="af833-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af833-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="af833-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="af833-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af833-112">See also</span></span>

- [<span data-ttu-id="af833-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="af833-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="af833-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="af833-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
