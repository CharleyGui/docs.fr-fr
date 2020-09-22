---
title: <message> Cette erreur peut résulter de la combinaison d’une référence de fichier et d’une référence de projet pour l’assembly <assemblyname>
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: cd2c00bda5b63abbd6bf7069ef28d0a812b22044
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873786"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="938d1-102">\<message> Cette erreur peut résulter de la combinaison d’une référence de fichier et d’une référence de projet pour l’assembly \<assemblyname></span><span class="sxs-lookup"><span data-stu-id="938d1-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>

<span data-ttu-id="938d1-103">\<message> Cette erreur peut également être due à la combinaison d’une référence de fichier et d’une référence de projet à l’assembly' \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="938d1-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="938d1-104">Dans ce cas, essayez de remplacer la référence de fichier à' \<assemblyfilename> 'dans le projet' \<projectname1> 'par une référence de projet à' \<projectname2> '.</span><span class="sxs-lookup"><span data-stu-id="938d1-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="938d1-105">Le code de votre projet accède à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur Visual Basic à résoudre la référence.</span><span class="sxs-lookup"><span data-stu-id="938d1-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="938d1-106">Pour accéder à un type défini dans un autre assembly, le compilateur Visual Basic doit avoir une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="938d1-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="938d1-107">Cette référence doit être unique et non équivoque et elle ne doit pas provoquer de références circulaires entre les projets.</span><span class="sxs-lookup"><span data-stu-id="938d1-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="938d1-108">**ID d’erreur :** BC30971</span><span class="sxs-lookup"><span data-stu-id="938d1-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="938d1-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="938d1-109">To correct this error</span></span>  
  
1. <span data-ttu-id="938d1-110">Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer.</span><span class="sxs-lookup"><span data-stu-id="938d1-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="938d1-111">Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="938d1-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="938d1-112">Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="938d1-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938d1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="938d1-113">See also</span></span>

- [<span data-ttu-id="938d1-114">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="938d1-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="938d1-115">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="938d1-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="938d1-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="938d1-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="938d1-117">Dépannage de références rompues</span><span class="sxs-lookup"><span data-stu-id="938d1-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
