---
title: L'espace de noms ou le type spécifié dans les Imports '<qualifiedelementname>' au niveau du projet ne contient aucun membre public ou est introuvable
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 54ee046cda998be8bd70e531918d6ab2a67d0494
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160117"
---
# <a name="bc40057-namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="bf9e5-102">BC40057 : l’espace de noms ou le type spécifié dans les importations au niveau du projet' \<qualifiedelementname> 'ne contient aucun membre public ou est introuvable</span><span class="sxs-lookup"><span data-stu-id="bf9e5-102">BC40057: Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="bf9e5-103">L’espace de noms ou le type spécifié dans les importations au niveau du projet' \<qualifiedelementname> 'ne contient aucun membre public ou est introuvable.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="bf9e5-104">Assurez-vous que l’espace de noms ou le type est défini et contient au moins un membre public.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="bf9e5-105">Assurez-vous que le nom d’alias ne contient pas d’autres alias.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-105">Make sure the alias name doesn't contain other aliases.</span></span>

 <span data-ttu-id="bf9e5-106">Une propriété d’importation d’un projet spécifie un élément conteneur qui est introuvable ou ne définit aucun `Public` membre.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

 <span data-ttu-id="bf9e5-107">Un *élément conteneur* peut être un espace de noms, une classe, une structure, un module, une interface ou une énumération.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="bf9e5-108">L’élément conteneur contient des membres, tels que des variables, des procédures ou d’autres éléments conteneurs.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

 <span data-ttu-id="bf9e5-109">L’objectif de l’importation est de permettre à votre code d’accéder à des membres de type ou d’espace de noms sans avoir à les qualifier.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="bf9e5-110">Votre projet peut également avoir besoin d’ajouter une référence à l’espace de noms ou au type.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="bf9e5-111">Pour plus d’informations, consultez « importation d’éléments contenants » dans les [références aux éléments déclarés](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9e5-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

 <span data-ttu-id="bf9e5-112">Si le compilateur ne peut pas trouver l’élément conteneur spécifié, il ne peut pas résoudre les références qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="bf9e5-113">S’il trouve l’élément mais que l’élément n’expose aucun `Public` membre, aucune référence ne peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="bf9e5-114">Dans les deux cas, il est inutile d’importer l’élément.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-114">In either case it is meaningless to import the element.</span></span>

 <span data-ttu-id="bf9e5-115">Vous utilisez le **Concepteur de projet** pour spécifier les éléments à importer.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="bf9e5-116">Utilisez la section **espaces de noms importés** de la page **références** .</span><span class="sxs-lookup"><span data-stu-id="bf9e5-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="bf9e5-117">Vous pouvez accéder au **Concepteur de projets** en double-cliquant sur l’icône **mon projet** dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>

 <span data-ttu-id="bf9e5-118">**ID d’erreur :** BC40057</span><span class="sxs-lookup"><span data-stu-id="bf9e5-118">**Error ID:** BC40057</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bf9e5-119">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bf9e5-119">To correct this error</span></span>

1. <span data-ttu-id="bf9e5-120">Ouvrez le **Concepteur de projets** et basculez vers la page de **référence** .</span><span class="sxs-lookup"><span data-stu-id="bf9e5-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>

2. <span data-ttu-id="bf9e5-121">Dans la section **espaces de noms importés** , vérifiez que l’élément conteneur est accessible à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>

3. <span data-ttu-id="bf9e5-122">Vérifiez que l’élément conteneur expose au moins un `Public` membre.</span><span class="sxs-lookup"><span data-stu-id="bf9e5-122">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf9e5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf9e5-123">See also</span></span>

- [<span data-ttu-id="bf9e5-124">Page Références, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf9e5-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="bf9e5-125">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="bf9e5-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="bf9e5-126">Public</span><span class="sxs-lookup"><span data-stu-id="bf9e5-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="bf9e5-127">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf9e5-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="bf9e5-128">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="bf9e5-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
