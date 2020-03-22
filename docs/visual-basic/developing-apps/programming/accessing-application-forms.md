---
title: Accès aux formulaires de l'application
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 332b6a7563160528b6c17210170af0db6e9bc0e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349237"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="89e97-102">Accès aux formulaires de l’application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89e97-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="89e97-103">L’objet `My.Forms` permet d’accéder facilement à une instance de chaque Windows Form déclaré dans le projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="89e97-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="89e97-104">Vous pouvez également utiliser les propriétés de l’objet `My.Application` pour accéder à l’écran de démarrage et au formulaire principal de l’application, et obtenir une liste des formulaires ouverts de l’application.</span><span class="sxs-lookup"><span data-stu-id="89e97-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="89e97-105">Tâches</span><span class="sxs-lookup"><span data-stu-id="89e97-105">Tasks</span></span>  

 <span data-ttu-id="89e97-106">Le tableau suivant donne des exemples montrant comment accéder aux formulaires d’une application.</span><span class="sxs-lookup"><span data-stu-id="89e97-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="89e97-107">À</span><span class="sxs-lookup"><span data-stu-id="89e97-107">To</span></span>|<span data-ttu-id="89e97-108">Consultez</span><span class="sxs-lookup"><span data-stu-id="89e97-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="89e97-109">Accéder à un formulaire à partir d’un autre formulaire d’une application.</span><span class="sxs-lookup"><span data-stu-id="89e97-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="89e97-110">My.Forms, objet</span><span class="sxs-lookup"><span data-stu-id="89e97-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="89e97-111">Afficher les titres de tous les formulaires ouverts de l’application.</span><span class="sxs-lookup"><span data-stu-id="89e97-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="89e97-112">Mettre à jour l’écran de démarrage avec les informations d’état au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="89e97-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="89e97-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e97-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="89e97-114">My.Forms, objet</span><span class="sxs-lookup"><span data-stu-id="89e97-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
