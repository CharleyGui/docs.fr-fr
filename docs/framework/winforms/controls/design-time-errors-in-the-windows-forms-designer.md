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
ms.openlocfilehash: b553dd6f6c5e760a671dea6400586d7074d49f5f
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211322"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="1ce72-102">Erreurs au moment du design dans le Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ce72-102">Design-Time Errors in the Windows Forms Designer</span></span>

<span data-ttu-id="1ce72-103">Cette rubrique explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Visual Studio lorsque le Concepteur de formulaires Windows ne parvient pas à charger.</span><span class="sxs-lookup"><span data-stu-id="1ce72-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="1ce72-104">Si cette liste d’erreurs s’affiche, ne l’interprétez pas comme un bogue du concepteur, mais comme une aide vous permettant de corriger les erreurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1ce72-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="1ce72-105">Avoir une connaissance élémentaire de cette liste d’erreurs vous aidera à déboguer vos applications en vous fournissant des informations détaillées sur les erreurs et en suggérant des solutions potentielles.</span><span class="sxs-lookup"><span data-stu-id="1ce72-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="1ce72-106">L’Interface de la liste d’erreurs au moment du design</span><span class="sxs-lookup"><span data-stu-id="1ce72-106">The Design-Time Error List Interface</span></span>

<span data-ttu-id="1ce72-107">Si le Concepteur Windows Forms ne parvient pas à se charger, une liste d’erreurs s’affiche dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="1ce72-108">Les erreurs sont regroupées en plusieurs catégories.</span><span class="sxs-lookup"><span data-stu-id="1ce72-108">The errors are grouped into categories.</span></span> <span data-ttu-id="1ce72-109">Par exemple, si vous avez quatre instances de variables non déclarées, celles-ci seront regroupées dans la même catégorie d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="1ce72-110">Chaque catégorie d’erreur comprend une brève description qui résume l’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="1ce72-111">Vous pouvez développer ou réduire une catégorie d’erreur en cliquant sur l’en-tête de la catégorie d’erreur ou en cliquant sur le chevron développer/réduire.</span><span class="sxs-lookup"><span data-stu-id="1ce72-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="1ce72-112">Lorsque vous développez une catégorie d’erreur, l’aide supplémentaire suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="1ce72-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="1ce72-113">Instances de cette erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-113">Instances of this error.</span></span>

- <span data-ttu-id="1ce72-114">Aide sur cette erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-114">Help with this error.</span></span>

- <span data-ttu-id="1ce72-115">Publications du forum sur cette erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="1ce72-116">Instances de cette erreur</span><span class="sxs-lookup"><span data-stu-id="1ce72-116">Instances of This Error</span></span>

<span data-ttu-id="1ce72-117">L’aide supplémentaire liste toutes les instances de l’erreur dans le projet en cours.</span><span class="sxs-lookup"><span data-stu-id="1ce72-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="1ce72-118">De nombreuses erreurs comprennent un emplacement exact au format suivant : *[nom du projet]* *[nom du formulaire]* Ligne :*[numéro de ligne]* Colonne :*[numéro de colonne]*.</span><span class="sxs-lookup"><span data-stu-id="1ce72-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="1ce72-119">Le lien **Accéder au code** vous conduit à l’endroit où l’erreur se produit dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1ce72-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="1ce72-120">Si une pile d’appels est associée à l’erreur, vous pouvez cliquer sur le lien **Afficher la pile des appels**, qui développe davantage l’erreur pour afficher la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="1ce72-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="1ce72-121">Examiner la pile peut permettre d’obtenir des informations de débogage utiles.</span><span class="sxs-lookup"><span data-stu-id="1ce72-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="1ce72-122">Par exemple, vous pouvez suivre les fonctions appelées avant que l’erreur ne se produise.</span><span class="sxs-lookup"><span data-stu-id="1ce72-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="1ce72-123">La pile des appels est sélectionnable ; vous pouvez donc la copier et l’enregistrer.</span><span class="sxs-lookup"><span data-stu-id="1ce72-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="1ce72-124">En Visual Basic, la liste d’erreurs au moment du design n’affiche pas plus d’une erreur, mais peut afficher plusieurs instances de la même erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="1ce72-125">En Visual C++, les erreurs n’ont pas de lien Accéder au code ou de lien vers les numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="1ce72-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="help-with-this-error"></a><span data-ttu-id="1ce72-126">Aide sur cette erreur</span><span class="sxs-lookup"><span data-stu-id="1ce72-126">Help with This Error</span></span>

<span data-ttu-id="1ce72-127">Si l’erreur contient un lien vers une rubrique d’aide MSDN associée, l’aide supplémentaire inclut un lien vers la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="1ce72-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="1ce72-128">Si vous cliquez sur le lien, la rubrique d’aide associée apparaît dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ce72-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="1ce72-129">Publications de forum sur cette erreur</span><span class="sxs-lookup"><span data-stu-id="1ce72-129">Forum posts about this error</span></span>

<span data-ttu-id="1ce72-130">L’aide supplémentaire inclut un lien vers des publications du forum MSDN associées à l’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="1ce72-131">La recherche dans les forums est effectuée en fonction de la chaîne du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="1ce72-132">Vous pouvez également effectuer une recherche dans les forums suivants :</span><span class="sxs-lookup"><span data-stu-id="1ce72-132">You can also try searching the following forums:</span></span>

- [<span data-ttu-id="1ce72-133">Forum Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ce72-133">Windows Forms Designer Forum</span></span>](https://go.microsoft.com/fwlink/?LinkId=203524)

- [<span data-ttu-id="1ce72-134">Forums Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ce72-134">Windows Forms Forums</span></span>](https://go.microsoft.com/fwlink/?LinkId=203523)

### <a name="ignore-and-continue"></a><span data-ttu-id="1ce72-135">Ignorer et continuer</span><span class="sxs-lookup"><span data-stu-id="1ce72-135">Ignore and Continue</span></span>

<span data-ttu-id="1ce72-136">Vous pouvez choisir d’ignorer l’erreur et de continuer à charger le concepteur.</span><span class="sxs-lookup"><span data-stu-id="1ce72-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="1ce72-137">Cette action peut entraîner un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="1ce72-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="1ce72-138">Par exemple, il est possible que les contrôles n’apparaissent pas sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="1ce72-138">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce72-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ce72-139">See also</span></span>

- <span data-ttu-id="1ce72-140">[Dépannage du développement au moment du Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="1ce72-140">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="1ce72-141">Dépannage de la création de contrôles et de composants</span><span class="sxs-lookup"><span data-stu-id="1ce72-141">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="1ce72-142">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="1ce72-142">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="1ce72-143">[Messages d’erreur du Concepteur Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1ce72-143">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
