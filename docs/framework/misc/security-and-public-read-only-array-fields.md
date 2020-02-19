---
title: Sécurité et champs de tableau en lecture seule publics
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452706"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="51623-102">Sécurité et champs de tableau en lecture seule publics</span><span class="sxs-lookup"><span data-stu-id="51623-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="51623-103">N’utilisez jamais de champs de tableau public en lecture seule à partir de bibliothèques managées pour définir le comportement de limite ou la sécurité de vos applications, car les champs de tableau public en lecture seule peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="51623-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51623-104">Notes</span><span class="sxs-lookup"><span data-stu-id="51623-104">Remarks</span></span>  

<span data-ttu-id="51623-105">Certaines classes .NET incluent des champs publics en lecture seule qui contiennent des paramètres de limite spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="51623-105">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="51623-106">Par exemple, le champ <xref:System.IO.Path.InvalidPathChars> est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="51623-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="51623-107">De nombreux champs similaires sont présents dans .NET.</span><span class="sxs-lookup"><span data-stu-id="51623-107">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="51623-108">Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peuvent être modifiées par votre code ou code qui partage le domaine d’application de votre code.</span><span class="sxs-lookup"><span data-stu-id="51623-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="51623-109">Vous ne devez pas utiliser des champs de tableau public en lecture seule comme celui-ci pour définir le comportement de limite de vos applications.</span><span class="sxs-lookup"><span data-stu-id="51623-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="51623-110">Si vous le faites, du code malveillant peut modifier les définitions des limites et utiliser votre code de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="51623-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="51623-111">Dans la version 2,0 et les versions ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser des champs de tableau publics.</span><span class="sxs-lookup"><span data-stu-id="51623-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="51623-112">Par exemple, au lieu d’utiliser le champ <xref:System.IO.Path.InvalidPathChars>, vous devez utiliser la méthode <xref:System.IO.Path.GetInvalidPathChars%2A>.</span><span class="sxs-lookup"><span data-stu-id="51623-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="51623-113">Notez que les types de .NET Framework n’utilisent pas les champs publics pour définir les types de limites en interne.</span><span class="sxs-lookup"><span data-stu-id="51623-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="51623-114">Au lieu de cela, le .NET Framework utilise des champs privés distincts.</span><span class="sxs-lookup"><span data-stu-id="51623-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="51623-115">La modification des valeurs de ces champs publics ne modifie pas le comportement des types de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51623-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51623-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51623-116">See also</span></span>

- [<span data-ttu-id="51623-117">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="51623-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
