---
title: My.Settings, objet
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350356"
---
# <a name="mysettings-object"></a><span data-ttu-id="28229-102">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="28229-102">My.Settings Object</span></span>
<span data-ttu-id="28229-103">Fournit des propriétés et des méthodes pour accéder aux paramètres de l’application.</span><span class="sxs-lookup"><span data-stu-id="28229-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28229-104">Notes</span><span class="sxs-lookup"><span data-stu-id="28229-104">Remarks</span></span>  
 <span data-ttu-id="28229-105">L’objet `My.Settings` fournit l’accès aux paramètres de l’application et vous permet de stocker et de récupérer dynamiquement des paramètres de propriété et d’autres informations pour votre application.</span><span class="sxs-lookup"><span data-stu-id="28229-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="28229-106">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="28229-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28229-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="28229-107">Properties</span></span>  
 <span data-ttu-id="28229-108">Les propriétés de l’objet `My.Settings` fournissent l’accès aux paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="28229-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="28229-109">Pour ajouter ou supprimer des paramètres, utilisez le **Concepteur de paramètres**.</span><span class="sxs-lookup"><span data-stu-id="28229-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="28229-110">Chaque paramètre a un **nom**, un **type**, une **étendue**et une **valeur**, et ces paramètres déterminent la façon dont la propriété pour accéder à chaque paramètre apparaît dans l’objet `My.Settings` :</span><span class="sxs-lookup"><span data-stu-id="28229-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="28229-111">**Nom** détermine le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="28229-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="28229-112">**Type** détermine le type de la propriété.</span><span class="sxs-lookup"><span data-stu-id="28229-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="28229-113">L' **étendue** indique si la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="28229-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="28229-114">Si la valeur est **application**, la propriété est en lecture seule ; Si la valeur est **User**, la propriété est en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="28229-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="28229-115">La **valeur** est la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="28229-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28229-116">Méthodes</span><span class="sxs-lookup"><span data-stu-id="28229-116">Methods</span></span>  
  
|<span data-ttu-id="28229-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="28229-117">Method</span></span>|<span data-ttu-id="28229-118">Description</span><span class="sxs-lookup"><span data-stu-id="28229-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="28229-119">Recharge les paramètres utilisateur à partir des dernières valeurs enregistrées.</span><span class="sxs-lookup"><span data-stu-id="28229-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="28229-120">Enregistre les paramètres utilisateur actuels.</span><span class="sxs-lookup"><span data-stu-id="28229-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="28229-121">L’objet `My.Settings` fournit également des propriétés et des méthodes avancées, héritées de la classe <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="28229-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="28229-122">Tâches</span><span class="sxs-lookup"><span data-stu-id="28229-122">Tasks</span></span>  
 <span data-ttu-id="28229-123">Le tableau suivant répertorie des exemples de tâches impliquant l’objet `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="28229-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="28229-124">Pour</span><span class="sxs-lookup"><span data-stu-id="28229-124">To</span></span>|<span data-ttu-id="28229-125">Consultez</span><span class="sxs-lookup"><span data-stu-id="28229-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="28229-126">Lire un paramètre d’application</span><span class="sxs-lookup"><span data-stu-id="28229-126">Read an application setting</span></span>|[<span data-ttu-id="28229-127">Guide pratique pour lire des paramètres d’application dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="28229-128">Modifier un paramètre utilisateur</span><span class="sxs-lookup"><span data-stu-id="28229-128">Change a user setting</span></span>|[<span data-ttu-id="28229-129">Guide pratique pour modifier les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="28229-130">Conserver les paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="28229-130">Persist user settings</span></span>|[<span data-ttu-id="28229-131">Guide pratique pour rendre persistants les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="28229-132">Créer une grille des propriétés pour les paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="28229-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="28229-133">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="28229-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="28229-134">Example</span></span>  
 <span data-ttu-id="28229-135">Cet exemple affiche la valeur du paramètre `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="28229-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="28229-136">Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="28229-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28229-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28229-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="28229-138">Guide pratique pour lire des paramètres d’application dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="28229-139">Guide pratique pour modifier les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="28229-140">Guide pratique pour rendre persistants les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="28229-141">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28229-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="28229-142">Gestion des paramètres d’une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="28229-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
