---
title: Sécurité et champs de tableau en lecture seule publics
description: Découvrez pourquoi vous devez éviter d’utiliser des champs de tableau en lecture seule publics pour définir le comportement de limite ou la sécurité de vos applications.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 0a6a82c2c88fe61bd34c0accb831f018cf8702fc
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281431"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="fc3a6-103">Sécurité et champs de tableau en lecture seule publics</span><span class="sxs-lookup"><span data-stu-id="fc3a6-103">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="fc3a6-104">N’utilisez jamais de champs de tableau public en lecture seule à partir de bibliothèques managées pour définir le comportement de limite ou la sécurité de vos applications, car les champs de tableau public en lecture seule peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3a6-105">Notes</span><span class="sxs-lookup"><span data-stu-id="fc3a6-105">Remarks</span></span>  

<span data-ttu-id="fc3a6-106">Certaines classes .NET incluent des champs publics en lecture seule qui contiennent des paramètres de limite spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="fc3a6-107">Par exemple, le <xref:System.IO.Path.InvalidPathChars> champ est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="fc3a6-108">De nombreux champs similaires sont présents dans .NET.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="fc3a6-109">Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peuvent être modifiées par votre code ou code qui partage le domaine d’application de votre code.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="fc3a6-110">Vous ne devez pas utiliser des champs de tableau public en lecture seule comme celui-ci pour définir le comportement de limite de vos applications.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="fc3a6-111">Si vous le faites, du code malveillant peut modifier les définitions des limites et utiliser votre code de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="fc3a6-112">Dans la version 2,0 et les versions ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser des champs de tableau publics.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="fc3a6-113">Par exemple, au lieu d’utiliser le <xref:System.IO.Path.InvalidPathChars> champ, vous devez utiliser la <xref:System.IO.Path.GetInvalidPathChars%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="fc3a6-114">Notez que les types de .NET Framework n’utilisent pas les champs publics pour définir les types de limites en interne.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="fc3a6-115">Au lieu de cela, le .NET Framework utilise des champs privés distincts.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="fc3a6-116">La modification des valeurs de ces champs publics ne modifie pas le comportement des types de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc3a6-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3a6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc3a6-117">See also</span></span>

- [<span data-ttu-id="fc3a6-118">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="fc3a6-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
