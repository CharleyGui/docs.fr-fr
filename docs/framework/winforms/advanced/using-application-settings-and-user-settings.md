---
title: Utilisation de paramètres d'application et de paramètres utilisateur
ms.date: 03/30/2017
description: Découvrez comment utiliser les paramètres de l’application et les paramètres utilisateur pour créer et accéder aux valeurs qui sont conservées entre les sessions d’exécution de l’application.
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903166"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="c047d-103">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="c047d-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="c047d-104">À partir de la .NET Framework 2,0, vous pouvez créer et accéder à des valeurs qui sont conservées entre les sessions d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="c047d-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="c047d-105">Ces valeurs sont appelées *paramètres*.</span><span class="sxs-lookup"><span data-stu-id="c047d-105">These values are called *settings*.</span></span> <span data-ttu-id="c047d-106">Les paramètres peuvent représenter des préférences utilisateur ou des informations importantes que l’application doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="c047d-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="c047d-107">Par exemple, vous pouvez créer une série de paramètres qui stockent les préférences utilisateur pour le modèle de couleurs d’une application.</span><span class="sxs-lookup"><span data-stu-id="c047d-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="c047d-108">Vous pouvez également stocker la chaîne de connexion qui spécifie une base de données que votre application utilise.</span><span class="sxs-lookup"><span data-stu-id="c047d-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="c047d-109">Les paramètres vous permettent de conserver les informations qui sont essentielles à l’application en dehors du code et de créer des profils qui stockent les préférences des utilisateurs individuels.</span><span class="sxs-lookup"><span data-stu-id="c047d-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="c047d-110">Les rubriques de cette section décrivent comment utiliser des paramètres au moment de la conception et de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c047d-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c047d-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c047d-111">In This Section</span></span>  
 [<span data-ttu-id="c047d-112">Guide pratique pour créer un nouveau paramètre au moment du design</span><span class="sxs-lookup"><span data-stu-id="c047d-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="c047d-113">Explique comment utiliser Visual Studio pour créer un nouveau paramètre pour une application.</span><span class="sxs-lookup"><span data-stu-id="c047d-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="c047d-114">Comment : modifier la valeur d'un paramètre existant au moment du design</span><span class="sxs-lookup"><span data-stu-id="c047d-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="c047d-115">Décrit comment utiliser Visual Studio pour modifier la valeur d’un paramètre existant.</span><span class="sxs-lookup"><span data-stu-id="c047d-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="c047d-116">Comment : modifier la valeur d'un paramètre entre des sessions d'application</span><span class="sxs-lookup"><span data-stu-id="c047d-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="c047d-117">Explique comment modifier la valeur d’un paramètre dans une application compilée entre des sessions d’application.</span><span class="sxs-lookup"><span data-stu-id="c047d-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="c047d-118">Comment : lire des paramètres au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="c047d-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="c047d-119">Décrit comment utiliser le code pour lire les paramètres avec C#.</span><span class="sxs-lookup"><span data-stu-id="c047d-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="c047d-120">Guide pratique pour écrire des paramètres utilisateur au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="c047d-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="c047d-121">Explique comment utiliser le code pour écrire et enregistrer les valeurs des paramètres utilisateur en C#.</span><span class="sxs-lookup"><span data-stu-id="c047d-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="c047d-122">Comment : ajouter plusieurs jeux de paramètres à votre application en C#</span><span class="sxs-lookup"><span data-stu-id="c047d-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="c047d-123">Explique comment ajouter plusieurs jeux de paramètres à une application avec C#.</span><span class="sxs-lookup"><span data-stu-id="c047d-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c047d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c047d-124">See also</span></span>

- [<span data-ttu-id="c047d-125">Paramètres d’application pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c047d-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
