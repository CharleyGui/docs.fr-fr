---
title: Un formulaire de démarrage n'a pas été spécifié
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409905"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="ac24a-102">Un formulaire de démarrage n'a pas été spécifié</span><span class="sxs-lookup"><span data-stu-id="ac24a-102">A startup form has not been specified</span></span>

<span data-ttu-id="ac24a-103">L’application utilise la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe mais ne spécifie pas le formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ac24a-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="ac24a-104">Cela peut se produire si la case à cocher **activer l’infrastructure** de l’application est activée dans le concepteur de projets, mais que le **formulaire de démarrage** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac24a-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="ac24a-105">Pour plus d'informations, consultez [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac24a-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ac24a-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ac24a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ac24a-107">Spécifiez un objet de démarrage pour l’application.</span><span class="sxs-lookup"><span data-stu-id="ac24a-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="ac24a-108">Pour plus d'informations, consultez [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac24a-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="ac24a-109">Substituez la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> méthode pour définir la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> propriété sur le formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="ac24a-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac24a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac24a-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="ac24a-111">Vue d'ensemble du modèle d'application Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac24a-111">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
