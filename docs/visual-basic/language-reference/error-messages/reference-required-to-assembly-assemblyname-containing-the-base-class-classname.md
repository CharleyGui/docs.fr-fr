---
title: Une référence à l'assembly '<assemblyname>' contenant la classe de base '<classname>' est requise
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: 07c09d0dfcb374b974fbda9099c4e85d6d054753
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870910"
---
# <a name="reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="85da0-102">Une référence à l'assembly '\<assemblyname>' contenant la classe de base '\<classname>' est requise</span><span class="sxs-lookup"><span data-stu-id="85da0-102">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="85da0-103">Une référence à l’assembly' \<assemblyname> 'contenant la classe de base' 'est requise \<classname> .</span><span class="sxs-lookup"><span data-stu-id="85da0-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="85da0-104">Ajoutez-en une à votre projet.</span><span class="sxs-lookup"><span data-stu-id="85da0-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="85da0-105">La classe est définie dans une bibliothèque de liens dynamiques (DLL) ou un assembly qui n’est pas directement référencé dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="85da0-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="85da0-106">Le compilateur Visual Basic requiert une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs DLL ou assemblys.</span><span class="sxs-lookup"><span data-stu-id="85da0-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="85da0-107">**ID d’erreur :** BC30007</span><span class="sxs-lookup"><span data-stu-id="85da0-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85da0-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="85da0-108">To correct this error</span></span>  
  
- <span data-ttu-id="85da0-109">Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.</span><span class="sxs-lookup"><span data-stu-id="85da0-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85da0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85da0-110">See also</span></span>

- [<span data-ttu-id="85da0-111">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="85da0-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="85da0-112">Dépannage de références rompues</span><span class="sxs-lookup"><span data-stu-id="85da0-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
