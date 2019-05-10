---
title: La valeur du type '<typename1>' ne peut pas être convertie en '<typename2>' (plusieurs références de fichier)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 7371cbd4fef4abced95744071ff222b40e160e3e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620312"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="074b6-102">Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >' (plusieurs références de fichier)</span><span class="sxs-lookup"><span data-stu-id="074b6-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="074b6-103">Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >'.</span><span class="sxs-lookup"><span data-stu-id="074b6-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="074b6-104">Incompatibilité de type peut être dû à la combinaison d’une référence de fichier pour '\<chemin_fichier1 >' dans le projet '\<nom_projet1 >' avec une référence de fichier à '\<chemin_fichier2 >' dans le projet '\<nom_projet2 >'.</span><span class="sxs-lookup"><span data-stu-id="074b6-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="074b6-105">Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu’elles se situent au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="074b6-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="074b6-106">Dans une situation où un projet fait plusieurs références de fichier à un assembly, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.</span><span class="sxs-lookup"><span data-stu-id="074b6-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="074b6-107">Chaque référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie d’un projet (généralement un fichier DLL).</span><span class="sxs-lookup"><span data-stu-id="074b6-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="074b6-108">Le compilateur ne peut pas garantir que les fichiers de sortie proviennent de la même source, ou qu’ils représentent la même version du même assembly.</span><span class="sxs-lookup"><span data-stu-id="074b6-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="074b6-109">Par conséquent, il ne peut pas garantir que les types dans les références différentes sont du même type, ou même que l’un peut être converti à l’autre.</span><span class="sxs-lookup"><span data-stu-id="074b6-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="074b6-110">Vous pouvez utiliser une référence de fichier unique si vous savez que les assemblys référencés ont la même identité d’assembly.</span><span class="sxs-lookup"><span data-stu-id="074b6-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="074b6-111">L’ *identité de l’assembly* comprend le nom de l’assembly, sa version, sa clé publique (le cas échéant) et sa culture.</span><span class="sxs-lookup"><span data-stu-id="074b6-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="074b6-112">Ces informations identifient de manière unique l’assembly.</span><span class="sxs-lookup"><span data-stu-id="074b6-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="074b6-113">**ID d’erreur :** BC30961</span><span class="sxs-lookup"><span data-stu-id="074b6-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="074b6-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="074b6-114">To correct this error</span></span>  
  
- <span data-ttu-id="074b6-115">Si les assemblys référencés ont la même identité de l’assembly, supprimez ou remplacez une des références de fichier afin qu’il soit uniquement une référence de fichier unique.</span><span class="sxs-lookup"><span data-stu-id="074b6-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="074b6-116">Si les assemblys référencés n’ont pas la même identité d’assembly, puis modifiez votre code afin qu’il ne tente pas de convertir un type dans un à un type dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="074b6-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074b6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="074b6-117">See also</span></span>

- [<span data-ttu-id="074b6-118">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="074b6-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="074b6-119">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="074b6-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
