---
title: Un formulaire de démarrage n'a pas été spécifié
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976191"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="9bb8f-102">Un formulaire de démarrage n'a pas été spécifié</span><span class="sxs-lookup"><span data-stu-id="9bb8f-102">A startup form has not been specified</span></span>

<span data-ttu-id="9bb8f-103">L’application utilise la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, mais ne spécifie pas le formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="9bb8f-104">Cela peut se produire si la case à cocher **activer l’infrastructure** de l’application est activée dans le concepteur de projets, mais que le **formulaire de démarrage** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="9bb8f-105">Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9bb8f-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bb8f-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9bb8f-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9bb8f-107">Spécifiez un objet de démarrage pour l’application.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="9bb8f-108">Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9bb8f-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="9bb8f-109">Substituez la méthode <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> pour définir la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> sur le formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="9bb8f-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb8f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bb8f-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="9bb8f-111">Vue d’ensemble du modèle d’application Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bb8f-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
