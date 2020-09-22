---
title: Une référence à l'assembly '<assemblyidentity>' contenant le type '<typename>' est requise, mais une référence adéquate n'a pas été trouvée en raison de l'ambiguïté entre les projets '<projectname1>' et '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ffc6b3c180c86abe272d56d0ecf3042d8181da59
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870901"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="90ec7-102">Une référence à l'assembly '\<assemblyidentity>' contenant le type '\<typename>' est requise, mais une référence adéquate n'a pas été trouvée en raison de l'ambiguïté entre les projets '\<projectname1>' et '\<projectname2>'</span><span class="sxs-lookup"><span data-stu-id="90ec7-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="90ec7-103">Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet.</span><span class="sxs-lookup"><span data-stu-id="90ec7-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="90ec7-104">Cependant, des références de projet désignent plusieurs assemblys définissant ce type.</span><span class="sxs-lookup"><span data-stu-id="90ec7-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="90ec7-105">Les projets cités produisent des assemblys de même nom.</span><span class="sxs-lookup"><span data-stu-id="90ec7-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="90ec7-106">Par conséquent, le compilateur ne peut pas déterminer quel assembly utiliser pour le type auquel vous accédez.</span><span class="sxs-lookup"><span data-stu-id="90ec7-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="90ec7-107">Pour accéder à un type défini dans un autre assembly, le compilateur Visual Basic doit avoir une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="90ec7-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="90ec7-108">Cette référence doit être unique et non équivoque et elle ne doit pas provoquer de références circulaires entre les projets.</span><span class="sxs-lookup"><span data-stu-id="90ec7-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="90ec7-109">**ID d’erreur :** BC30969</span><span class="sxs-lookup"><span data-stu-id="90ec7-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90ec7-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="90ec7-110">To correct this error</span></span>  
  
1. <span data-ttu-id="90ec7-111">Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer.</span><span class="sxs-lookup"><span data-stu-id="90ec7-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="90ec7-112">Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="90ec7-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="90ec7-113">Dans vos propriétés de projet, ajoutez une référence au fichier qui contient l’assembly qui définit le type que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="90ec7-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ec7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90ec7-114">See also</span></span>

- [<span data-ttu-id="90ec7-115">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="90ec7-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="90ec7-116">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="90ec7-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="90ec7-117">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="90ec7-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="90ec7-118">Dépannage de références rompues</span><span class="sxs-lookup"><span data-stu-id="90ec7-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
