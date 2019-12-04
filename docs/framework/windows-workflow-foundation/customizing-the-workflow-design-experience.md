---
title: Personnalisation de l'expérience de conception de workflow
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 27be398d874747b65ae051224070d3f40f1fbbb0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715135"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="ff1fa-102">Personnalisation de l'expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="ff1fa-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="ff1fa-103">Les scénarios de conception d’activités personnalisées et de réhébergement de Windows Concepteur de flux de travail ont été considérablement simplifiés dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-103">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="ff1fa-104">Le développement et le déploiement sont maintenant à la fois plus facile et plus souple.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="ff1fa-105">La principale modification de l’infrastructure est que le nouveau modèle de programmation de concepteur d’activités repose sur Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ff1fa-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="ff1fa-106">Cela vous donne la possibilité de définir des concepteurs d’activités de façon déclarative et de réhéberger les Concepteur de flux de travail dans d’autres applications avec une comparaison simple.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-106">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="ff1fa-107">Lors du réhébergement, un éditeur d'expressions personnalisé peut être développé pour prendre en charge IntelliSense ou un domaine d'expression simplifié.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="ff1fa-108">L’intégration à Windows Communication Foundation (WCF) est devenue plus transparente grâce à l’utilisation des services de Workflow.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="ff1fa-109">Les concepteurs d'activités personnalisées et l'arborescence d'éléments de modèle peuvent être utilisés pour améliorer les expériences au moment du design dans les concepteurs de workflow réhébergés.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ff1fa-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ff1fa-110">In This Section</span></span>

 [<span data-ttu-id="ff1fa-111">Utilisation de concepteurs d’activités et de modèles d’activité personnalisés</span><span class="sxs-lookup"><span data-stu-id="ff1fa-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="ff1fa-112">Explique comment créer de nouveaux concepteurs d'activités et modèles d'activité personnalisés.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="ff1fa-113">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="ff1fa-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="ff1fa-114">Décrit comment réhéberger les Concepteur de flux de travail Windows en dehors de Visual Studio et comment afficher les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-114">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="ff1fa-115">Utilisation d’un éditeur d’expressions personnalisé</span><span class="sxs-lookup"><span data-stu-id="ff1fa-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="ff1fa-116">Décrit comment implémenter un éditeur d’expressions personnalisé à utiliser avec les concepteurs de workflow réhébergés en dehors de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="ff1fa-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="ff1fa-117">Reference</span><span class="sxs-lookup"><span data-stu-id="ff1fa-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="ff1fa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff1fa-118">See also</span></span>

- [<span data-ttu-id="ff1fa-119">Extension de Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="ff1fa-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="ff1fa-120">Concepteur</span><span class="sxs-lookup"><span data-stu-id="ff1fa-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="ff1fa-121">Concepteurs d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="ff1fa-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="ff1fa-122">Réhébergement du concepteur</span><span class="sxs-lookup"><span data-stu-id="ff1fa-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
