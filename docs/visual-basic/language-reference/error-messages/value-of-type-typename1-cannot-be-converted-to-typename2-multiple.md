---
title: La valeur du type '<typename1>' ne peut pas être convertie en '<typename2>' (plusieurs références de fichier)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406584"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="24d7a-102">La valeur du type '\<typename1>' ne peut pas être convertie en '\<typename2>' (plusieurs références de fichier)</span><span class="sxs-lookup"><span data-stu-id="24d7a-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="24d7a-103">Impossible de convertir la valeur de type' ' \<typename1> en' \<typename2> '.</span><span class="sxs-lookup"><span data-stu-id="24d7a-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="24d7a-104">Une incompatibilité de type peut être due à la combinaison d’une référence de fichier à' \<filepath1> 'dans le projet' \<projectname1> 'avec une référence de fichier à' \<filepath2> 'dans le projet' \<projectname2> '.</span><span class="sxs-lookup"><span data-stu-id="24d7a-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="24d7a-105">Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu’elles se situent au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="24d7a-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="24d7a-106">Dans le cas où un projet crée plusieurs références de fichier à un assembly, le compilateur ne peut pas garantir qu’un type peut être converti en un autre.</span><span class="sxs-lookup"><span data-stu-id="24d7a-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="24d7a-107">Chaque référence de fichier spécifie un chemin d’accès et un nom de fichier pour le fichier de sortie d’un projet (en général, un fichier DLL).</span><span class="sxs-lookup"><span data-stu-id="24d7a-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="24d7a-108">Le compilateur ne peut pas garantir que les fichiers de sortie proviennent de la même source, ou qu’ils représentent la même version du même assembly.</span><span class="sxs-lookup"><span data-stu-id="24d7a-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="24d7a-109">Par conséquent, il ne peut pas garantir que les types des différentes références sont du même type, ou qu’il peut être converti en l’un l’autre.</span><span class="sxs-lookup"><span data-stu-id="24d7a-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="24d7a-110">Vous pouvez utiliser une référence de fichier unique si vous savez que les assemblys référencés ont la même identité d’assembly.</span><span class="sxs-lookup"><span data-stu-id="24d7a-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="24d7a-111">L' *identité de l’assembly* comprend le nom de l’assembly, sa version, sa clé publique, le cas échéant, et la culture.</span><span class="sxs-lookup"><span data-stu-id="24d7a-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="24d7a-112">Ces informations identifient de manière unique l’assembly.</span><span class="sxs-lookup"><span data-stu-id="24d7a-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="24d7a-113">**ID d’erreur :** BC30961</span><span class="sxs-lookup"><span data-stu-id="24d7a-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24d7a-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="24d7a-114">To correct this error</span></span>  
  
- <span data-ttu-id="24d7a-115">Si les assemblys référencés ont la même identité d’assembly, supprimez ou remplacez l’une des références de fichier pour qu’il n’y ait qu’une seule référence de fichier.</span><span class="sxs-lookup"><span data-stu-id="24d7a-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="24d7a-116">Si les assemblys référencés n’ont pas la même identité d’assembly, modifiez votre code afin qu’il n’essaie pas de convertir un type en un type dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="24d7a-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d7a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24d7a-117">See also</span></span>

- [<span data-ttu-id="24d7a-118">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24d7a-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="24d7a-119">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="24d7a-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
