---
title: <permission> -Guide de programmation C#
description: En savoir plus sur le XML <permission> balise. Cette balise vous permet de documenter l’accès d’un membre, tandis que la classe PermissionSet vous permet de spécifier l’accès à un membre.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381721"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="4b176-105">\<permission>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4b176-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b176-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b176-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="4b176-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b176-107">Parameters</span></span>

- <span data-ttu-id="4b176-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="4b176-108">cref = " `member`"</span></span>

  <span data-ttu-id="4b176-109">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="4b176-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4b176-110">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b176-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4b176-111">Le *membre* doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="4b176-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="4b176-112">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="4b176-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="4b176-113">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="4b176-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b176-114">Notes</span><span class="sxs-lookup"><span data-stu-id="4b176-114">Remarks</span></span>

<span data-ttu-id="4b176-115">La `<permission>` balise vous permet de documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="4b176-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="4b176-116">La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="4b176-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="4b176-117">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="4b176-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4b176-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b176-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="4b176-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b176-119">See also</span></span>

- [<span data-ttu-id="4b176-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4b176-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4b176-121">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="4b176-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
