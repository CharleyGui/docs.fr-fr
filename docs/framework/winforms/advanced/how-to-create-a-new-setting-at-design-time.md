---
title: 'Procédure : créer un paramètre au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037903"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="cb31a-102">Procédure : Créer un nouveau paramètre au moment du design</span><span class="sxs-lookup"><span data-stu-id="cb31a-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="cb31a-103">Vous pouvez créer un nouveau paramètre au moment du design à l’aide du concepteur de paramètres dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb31a-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="cb31a-104">Le concepteur de paramètres est une interface de style grille qui vous permet de créer de nouveaux paramètres et de spécifier des propriétés pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb31a-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="cb31a-105">Vous devez spécifier le nom, la valeur, le type et l’étendue de vos nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb31a-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="cb31a-106">Une fois qu’un paramètre est créé, il est accessible dans le code.</span><span class="sxs-lookup"><span data-stu-id="cb31a-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="cb31a-107">Créer un nouveau paramètre au moment du design en C\#</span><span class="sxs-lookup"><span data-stu-id="cb31a-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="cb31a-108">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb31a-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="cb31a-109">Dans **Explorateur de solutions**, développez le nœud **Propriétés** de votre projet.</span><span class="sxs-lookup"><span data-stu-id="cb31a-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="cb31a-110">Double-cliquez sur le fichier. Settings dans lequel vous souhaitez ajouter un nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="cb31a-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="cb31a-111">Le nom par défaut de ce fichier est Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="cb31a-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="cb31a-112">Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="cb31a-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="cb31a-113">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="cb31a-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="cb31a-114">Créer un nouveau paramètre au moment du design dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb31a-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="cb31a-115">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb31a-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="cb31a-116">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de votre projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cb31a-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="cb31a-117">Dans la page **Propriétés** , sélectionnez l’onglet **paramètres** .</span><span class="sxs-lookup"><span data-stu-id="cb31a-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="cb31a-118">Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="cb31a-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="cb31a-119">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="cb31a-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb31a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb31a-120">See also</span></span>

- [<span data-ttu-id="cb31a-121">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="cb31a-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="cb31a-122">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="cb31a-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="cb31a-123">Guide pratique pour Modifier la valeur d’un paramètre existant au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="cb31a-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
