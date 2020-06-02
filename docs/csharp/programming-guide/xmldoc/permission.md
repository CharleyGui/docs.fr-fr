---
title: <permission> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287270"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="7fa2d-102">\<permission>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7fa2d-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fa2d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa2d-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="7fa2d-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7fa2d-104">Parameters</span></span>

- <span data-ttu-id="7fa2d-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="7fa2d-105">cref = " `member`"</span></span>

  <span data-ttu-id="7fa2d-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="7fa2d-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="7fa2d-108">Le *membre* doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="7fa2d-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="7fa2d-109">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="7fa2d-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="7fa2d-110">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fa2d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7fa2d-111">Remarks</span></span>

<span data-ttu-id="7fa2d-112">La `<permission>` balise vous permet de documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-112">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="7fa2d-113">La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="7fa2d-114">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="7fa2d-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7fa2d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="7fa2d-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="7fa2d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fa2d-116">See also</span></span>

- [<span data-ttu-id="7fa2d-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7fa2d-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7fa2d-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="7fa2d-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
