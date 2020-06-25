---
title: 'Comment : créer un nouveau paramètre au moment du design'
description: Découvrez comment créer un paramètre de Windows Forms au moment de la conception à l’aide du concepteur de paramètres dans Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325845"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="85147-103">Comment : créer un nouveau paramètre au moment du design</span><span class="sxs-lookup"><span data-stu-id="85147-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="85147-104">Vous pouvez créer un nouveau paramètre au moment du design à l’aide du concepteur de paramètres dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85147-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="85147-105">Le concepteur de paramètres est une interface de style grille qui vous permet de créer de nouveaux paramètres et de spécifier des propriétés pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="85147-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="85147-106">Vous devez spécifier le nom, la valeur, le type et l’étendue de vos nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="85147-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="85147-107">Une fois qu’un paramètre est créé, il est accessible dans le code.</span><span class="sxs-lookup"><span data-stu-id="85147-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="85147-108">Créer un nouveau paramètre au moment du design en C\#</span><span class="sxs-lookup"><span data-stu-id="85147-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="85147-109">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85147-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="85147-110">Dans **Explorateur de solutions**, développez le nœud **Propriétés** de votre projet.</span><span class="sxs-lookup"><span data-stu-id="85147-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="85147-111">Double-cliquez sur le fichier. Settings dans lequel vous souhaitez ajouter un nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="85147-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="85147-112">Le nom par défaut de ce fichier est Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="85147-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="85147-113">Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="85147-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="85147-114">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="85147-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="85147-115">Créer un nouveau paramètre au moment du design dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85147-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="85147-116">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85147-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="85147-117">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de votre projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="85147-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="85147-118">Dans la page **Propriétés** , sélectionnez l’onglet **paramètres** .</span><span class="sxs-lookup"><span data-stu-id="85147-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="85147-119">Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="85147-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="85147-120">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="85147-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="85147-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85147-121">See also</span></span>

- [<span data-ttu-id="85147-122">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="85147-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="85147-123">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="85147-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="85147-124">Comment : modifier la valeur d'un paramètre existant au moment du design</span><span class="sxs-lookup"><span data-stu-id="85147-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
