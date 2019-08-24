---
title: Erreurs au moment du design dans le Concepteur Windows Forms
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015969"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="7f965-102">Erreurs au moment du design dans le Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f965-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="7f965-103">Cette rubrique explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Visual Studio lorsque le chargement du Concepteur Windows Forms échoue.</span><span class="sxs-lookup"><span data-stu-id="7f965-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="7f965-104">Si cette liste d’erreurs s’affiche, ne l’interprétez pas comme un bogue du concepteur, mais comme une aide vous permettant de corriger les erreurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="7f965-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="7f965-105">Avoir une connaissance élémentaire de cette liste d’erreurs vous aidera à déboguer vos applications en vous fournissant des informations détaillées sur les erreurs et en suggérant des solutions potentielles.</span><span class="sxs-lookup"><span data-stu-id="7f965-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="7f965-106">Interface de liste d’erreurs au moment du design</span><span class="sxs-lookup"><span data-stu-id="7f965-106">The design-time error list interface</span></span>

<span data-ttu-id="7f965-107">Si le Concepteur Windows Forms ne parvient pas à se charger, une liste d’erreurs apparaît dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="7f965-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="7f965-108">Les erreurs sont regroupées en plusieurs catégories.</span><span class="sxs-lookup"><span data-stu-id="7f965-108">The errors are grouped into categories.</span></span> <span data-ttu-id="7f965-109">Par exemple, si vous avez quatre instances de variables non déclarées, celles-ci seront regroupées dans la même catégorie d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="7f965-110">Chaque catégorie d’erreur comprend une brève description qui résume l’erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="7f965-111">Vous pouvez développer ou réduire une catégorie d’erreur en cliquant sur l’en-tête de la catégorie d’erreur ou en cliquant sur le chevron développer/réduire.</span><span class="sxs-lookup"><span data-stu-id="7f965-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="7f965-112">Lorsque vous développez une catégorie d’erreur, l’aide supplémentaire suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="7f965-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="7f965-113">Instances de cette erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-113">Instances of this error.</span></span>

- <span data-ttu-id="7f965-114">Aide sur cette erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-114">Help with this error.</span></span>

- <span data-ttu-id="7f965-115">Publications du forum sur cette erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="7f965-116">Instances de cette erreur</span><span class="sxs-lookup"><span data-stu-id="7f965-116">Instances of this error</span></span>

<span data-ttu-id="7f965-117">L’aide supplémentaire liste toutes les instances de l’erreur dans le projet en cours.</span><span class="sxs-lookup"><span data-stu-id="7f965-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="7f965-118">De nombreuses erreurs comprennent un emplacement exact au format suivant : *[nom du projet]* *[nom du formulaire]* Ligne : *[numéro de ligne]* Colonne : *[numéro de colonne]* .</span><span class="sxs-lookup"><span data-stu-id="7f965-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="7f965-119">Le lien **Accéder au code** vous conduit à l’endroit où l’erreur se produit dans votre code.</span><span class="sxs-lookup"><span data-stu-id="7f965-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="7f965-120">Si une pile d’appels est associée à l’erreur, vous pouvez cliquer sur le lien **Afficher la pile des appels**, qui développe davantage l’erreur pour afficher la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="7f965-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="7f965-121">Examiner la pile peut permettre d’obtenir des informations de débogage utiles.</span><span class="sxs-lookup"><span data-stu-id="7f965-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="7f965-122">Par exemple, vous pouvez suivre les fonctions appelées avant que l’erreur ne se produise.</span><span class="sxs-lookup"><span data-stu-id="7f965-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="7f965-123">La pile des appels est sélectionnable ; vous pouvez donc la copier et l’enregistrer.</span><span class="sxs-lookup"><span data-stu-id="7f965-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="7f965-124">En Visual Basic, la liste d’erreurs au moment du design n’affiche pas plus d’une erreur, mais peut afficher plusieurs instances de la même erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="7f965-125">En Visual C++, les erreurs n’ont pas de lien Accéder au code ou de lien vers les numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="7f965-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="7f965-126">Publications de forum sur cette erreur</span><span class="sxs-lookup"><span data-stu-id="7f965-126">Forum posts about this error</span></span>

<span data-ttu-id="7f965-127">L’aide supplémentaire comprend un lien vers des publications de Forum relatives à l’erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="7f965-128">La recherche dans les forums est effectuée en fonction de la chaîne du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7f965-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="7f965-129">Vous pouvez également essayer d’effectuer une recherche sur les forums suivants:</span><span class="sxs-lookup"><span data-stu-id="7f965-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="7f965-130">Forum Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f965-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="7f965-131">Forum Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f965-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="7f965-132">Ignorer et continuer</span><span class="sxs-lookup"><span data-stu-id="7f965-132">Ignore and continue</span></span>

<span data-ttu-id="7f965-133">Vous pouvez choisir d’ignorer l’erreur et de continuer à charger le concepteur.</span><span class="sxs-lookup"><span data-stu-id="7f965-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="7f965-134">Cette action peut entraîner un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="7f965-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="7f965-135">Par exemple, il est possible que les contrôles n’apparaissent pas sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="7f965-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f965-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f965-136">See also</span></span>

- <span data-ttu-id="7f965-137">[Dépannage du développement au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7f965-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="7f965-138">Dépannage de la création de contrôles et de composants</span><span class="sxs-lookup"><span data-stu-id="7f965-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="7f965-139">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="7f965-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="7f965-140">[Messages d’erreur du Concepteur Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7f965-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
