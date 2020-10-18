---
title: Une référence à l'assembly '<assemblyname>' contenant la classe de base '<classname>' est requise
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162334"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="ca5da-102">BC30007 : une référence à l’assembly' \<assemblyname> 'contenant la classe de base' 'est requise \<classname></span><span class="sxs-lookup"><span data-stu-id="ca5da-102">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="ca5da-103">Une référence à l’assembly' \<assemblyname> 'contenant la classe de base' 'est requise \<classname> .</span><span class="sxs-lookup"><span data-stu-id="ca5da-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="ca5da-104">Ajoutez-en une à votre projet.</span><span class="sxs-lookup"><span data-stu-id="ca5da-104">Add one to your project.</span></span>

 <span data-ttu-id="ca5da-105">La classe est définie dans une bibliothèque de liens dynamiques (DLL) ou un assembly qui n’est pas directement référencé dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="ca5da-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="ca5da-106">Le compilateur Visual Basic requiert une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs DLL ou assemblys.</span><span class="sxs-lookup"><span data-stu-id="ca5da-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="ca5da-107">**ID d’erreur :** BC30007</span><span class="sxs-lookup"><span data-stu-id="ca5da-107">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ca5da-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ca5da-108">To correct this error</span></span>

- <span data-ttu-id="ca5da-109">Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.</span><span class="sxs-lookup"><span data-stu-id="ca5da-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca5da-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca5da-110">See also</span></span>

- [<span data-ttu-id="ca5da-111">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="ca5da-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="ca5da-112">Dépannage de références rompues</span><span class="sxs-lookup"><span data-stu-id="ca5da-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
