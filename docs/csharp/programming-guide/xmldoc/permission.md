---
title: <permission> - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 454928d5dfd023639bc68f194f2f5ec9e2d7dc22
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523398"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="54536-102">\<permission> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="54536-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="54536-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54536-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="54536-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54536-104">Parameters</span></span>  
 <span data-ttu-id="54536-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="54536-105">cref = " `member`"</span></span>  
 <span data-ttu-id="54536-106">Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="54536-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="54536-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="54536-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="54536-108">Le *membre* doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="54536-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="54536-109">Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="54536-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="54536-110">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="54536-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54536-111">Notes</span><span class="sxs-lookup"><span data-stu-id="54536-111">Remarks</span></span>  
 <span data-ttu-id="54536-112">La balise \<permission> vous permet de documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="54536-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="54536-113">La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="54536-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="54536-114">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="54536-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54536-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="54536-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="54536-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54536-116">See also</span></span>

- [<span data-ttu-id="54536-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="54536-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="54536-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="54536-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
