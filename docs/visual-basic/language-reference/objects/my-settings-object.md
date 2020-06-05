---
title: My.Settings, objet
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372399"
---
# <a name="mysettings-object"></a><span data-ttu-id="c19ac-102">My.Settings, objet</span><span class="sxs-lookup"><span data-stu-id="c19ac-102">My.Settings Object</span></span>
<span data-ttu-id="c19ac-103">Fournit des propriétés et des méthodes pour accéder aux paramètres de l’application.</span><span class="sxs-lookup"><span data-stu-id="c19ac-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c19ac-104">Notes</span><span class="sxs-lookup"><span data-stu-id="c19ac-104">Remarks</span></span>  
 <span data-ttu-id="c19ac-105">L' `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et de récupérer dynamiquement des paramètres de propriété et d’autres informations pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c19ac-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="c19ac-106">Pour plus d’informations, consultez [Gestion des paramètres d’une application (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c19ac-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c19ac-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c19ac-107">Properties</span></span>  
 <span data-ttu-id="c19ac-108">Les propriétés de l’objet `My.Settings` fournissent l’accès aux paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="c19ac-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="c19ac-109">Pour ajouter ou supprimer des paramètres, utilisez le **Concepteur de paramètres**.</span><span class="sxs-lookup"><span data-stu-id="c19ac-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="c19ac-110">Chaque paramètre a un **nom**, un **type**, une **étendue**et une **valeur**, et ces paramètres déterminent la façon dont la propriété pour accéder à chaque paramètre apparaît dans l' `My.Settings` objet :</span><span class="sxs-lookup"><span data-stu-id="c19ac-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="c19ac-111">**Nom** détermine le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c19ac-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="c19ac-112">**Type** détermine le type de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c19ac-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="c19ac-113">L' **étendue** indique si la propriété est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="c19ac-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="c19ac-114">Si la valeur est **application**, la propriété est en lecture seule ; Si la valeur est **User**, la propriété est en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="c19ac-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="c19ac-115">La **valeur** est la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c19ac-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c19ac-116">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c19ac-116">Methods</span></span>  
  
|<span data-ttu-id="c19ac-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="c19ac-117">Method</span></span>|<span data-ttu-id="c19ac-118">Description</span><span class="sxs-lookup"><span data-stu-id="c19ac-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="c19ac-119">Recharge les paramètres utilisateur à partir des dernières valeurs enregistrées.</span><span class="sxs-lookup"><span data-stu-id="c19ac-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="c19ac-120">Enregistre les paramètres utilisateur actuels.</span><span class="sxs-lookup"><span data-stu-id="c19ac-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="c19ac-121">L' `My.Settings` objet fournit également des propriétés et des méthodes avancées, héritées de la <xref:System.Configuration.ApplicationSettingsBase> classe.</span><span class="sxs-lookup"><span data-stu-id="c19ac-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c19ac-122">Tâches</span><span class="sxs-lookup"><span data-stu-id="c19ac-122">Tasks</span></span>  
 <span data-ttu-id="c19ac-123">Le tableau suivant répertorie des exemples de tâches impliquant l' `My.Settings` objet.</span><span class="sxs-lookup"><span data-stu-id="c19ac-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="c19ac-124">À</span><span class="sxs-lookup"><span data-stu-id="c19ac-124">To</span></span>|<span data-ttu-id="c19ac-125">Consultez</span><span class="sxs-lookup"><span data-stu-id="c19ac-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="c19ac-126">Lire un paramètre d’application</span><span class="sxs-lookup"><span data-stu-id="c19ac-126">Read an application setting</span></span>|[<span data-ttu-id="c19ac-127">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-127">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="c19ac-128">Modifier un paramètre utilisateur</span><span class="sxs-lookup"><span data-stu-id="c19ac-128">Change a user setting</span></span>|[<span data-ttu-id="c19ac-129">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-129">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="c19ac-130">Conserver les paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="c19ac-130">Persist user settings</span></span>|[<span data-ttu-id="c19ac-131">Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-131">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="c19ac-132">Créer une grille des propriétés pour les paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="c19ac-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="c19ac-133">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="c19ac-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="c19ac-134">Example</span></span>  
 <span data-ttu-id="c19ac-135">Cet exemple affiche la valeur du paramètre `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="c19ac-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="c19ac-136">Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="c19ac-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19ac-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c19ac-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="c19ac-138">Guide pratique pour lire des paramètres d’application en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-138">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="c19ac-139">Guide pratique pour modifier les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-139">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="c19ac-140">Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-140">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="c19ac-141">Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c19ac-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="c19ac-142">Gestion des paramètres d'une application (.NET)</span><span class="sxs-lookup"><span data-stu-id="c19ac-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
