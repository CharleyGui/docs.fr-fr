---
title: Une erreur inattendue s'est produite parce qu'une ressource de système d'exploitation requise pour le démarrage de l'instance unique ne peut pas être acquise
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 8130eee93ab5c14043283c28f522da53f9047e85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646886"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="4f0d0-102">Une erreur inattendue s'est produite parce qu'une ressource de système d'exploitation requise pour le démarrage de l'instance unique ne peut pas être acquise</span><span class="sxs-lookup"><span data-stu-id="4f0d0-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="4f0d0-103">L'application n'a pas pu obtenir une ressource nécessaire du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="4f0d0-104">Ce problème peut avoir certaines des causes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f0d0-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="4f0d0-105">L'application n'est pas autorisée à créer des objets de système d'exploitation nommés.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="4f0d0-106">Le Common Language Runtime n'est pas autorisé à créer des fichiers mappés sur la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="4f0d0-107">L'application doit accéder à un objet de système d'exploitation, mais un autre processus l'utilise.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f0d0-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="4f0d0-108">To correct this error</span></span>  
  
1. <span data-ttu-id="4f0d0-109">Vérifiez que l'application dispose d'autorisations suffisantes pour créer des objets de système d'exploitation nommés.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="4f0d0-110">Veillez à ce que le Common Language Runtime dispose d'autorisations suffisantes pour créer des fichiers mappés sur la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="4f0d0-111">Redémarrez l'ordinateur pour annuler tout processus susceptible d'utiliser la ressource permettant de se connecter à l'application de l'instance d'origine.</span><span class="sxs-lookup"><span data-stu-id="4f0d0-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="4f0d0-112">Notez les circonstances dans lesquelles l'erreur s'est produite, puis contactez les services de support technique Microsoft</span><span class="sxs-lookup"><span data-stu-id="4f0d0-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0d0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f0d0-113">See also</span></span>

- [<span data-ttu-id="4f0d0-114">Page Application, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f0d0-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="4f0d0-115">Principes de base du débogueur</span><span class="sxs-lookup"><span data-stu-id="4f0d0-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="4f0d0-116">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="4f0d0-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
