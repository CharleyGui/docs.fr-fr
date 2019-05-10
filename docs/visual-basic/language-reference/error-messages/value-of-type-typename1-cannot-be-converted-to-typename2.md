---
title: La valeur de type '<typename1>' ne peut pas être convertie en '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 027cccc9ad406d5bc2fd686ddeb4c674dc8f3c90
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621202"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="72461-102">Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >'</span><span class="sxs-lookup"><span data-stu-id="72461-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="72461-103">Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >'.</span><span class="sxs-lookup"><span data-stu-id="72461-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="72461-104">Incompatibilité de type peut être dû à la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<nom_assembly >'.</span><span class="sxs-lookup"><span data-stu-id="72461-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="72461-105">Essayez de remplacer la référence de fichier à '\<filepath >' dans le projet '\<nom_projet1 >' avec une référence de projet à '\<nom_projet2 >'.</span><span class="sxs-lookup"><span data-stu-id="72461-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="72461-106">Dans une situation où un projet fait une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.</span><span class="sxs-lookup"><span data-stu-id="72461-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="72461-107">Le pseudo-code suivant illustre une situation qui peut générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="72461-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="72461-108">Projet `P1` établit une référence de projet indirecte via le projet `P2` au projet `P3`et également une référence de fichier directe à `P3`.</span><span class="sxs-lookup"><span data-stu-id="72461-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="72461-109">La déclaration de `commonObject` utilise la référence de fichier à `P3`, tandis que l’appel à `P2.getCommonClass` utilise la référence de projet `P3`.</span><span class="sxs-lookup"><span data-stu-id="72461-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="72461-110">Le problème dans ce cas est que la référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie de `P3` (en général, p3.dll), tandis que les références de projet identifient le projet source (`P3`) par le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="72461-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="72461-111">Pour cette raison, le compilateur ne peut pas garantir que le type `P3.commonClass` provient le même code source, les deux références différentes.</span><span class="sxs-lookup"><span data-stu-id="72461-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="72461-112">Cette situation se produit généralement lorsque les références de projet et les références de fichier sont combinés.</span><span class="sxs-lookup"><span data-stu-id="72461-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="72461-113">Dans l’illustration précédente, le problème se produirait pas si `P1` crée une référence de projet directe pour `P3` au lieu d’une référence de fichier.</span><span class="sxs-lookup"><span data-stu-id="72461-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="72461-114">**ID d’erreur :** BC30955</span><span class="sxs-lookup"><span data-stu-id="72461-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72461-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="72461-115">To correct this error</span></span>  
  
- <span data-ttu-id="72461-116">Modifiez la référence de fichier à une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="72461-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72461-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72461-117">See also</span></span>

- [<span data-ttu-id="72461-118">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72461-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="72461-119">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="72461-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
