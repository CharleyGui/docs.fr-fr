---
title: Personnalisation de l'expérience de conception de workflow
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141928"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="f20f8-102">Personnalisation de l'expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="f20f8-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="f20f8-103">Les scénarios de conception d’activités personnalisées et de réhébergement du [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ont été considérablement simplifiés dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f20f8-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="f20f8-104">Le développement et le déploiement sont maintenant à la fois plus facile et plus souple.</span><span class="sxs-lookup"><span data-stu-id="f20f8-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="f20f8-105">La principale modification de l’infrastructure est que le nouveau modèle de programmation de concepteur d’activités repose sur Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f20f8-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="f20f8-106">Cela vous permet de définir des concepteurs d'activités de façon déclarative et de réhéberger le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans d'autres applications en toute simplicité.</span><span class="sxs-lookup"><span data-stu-id="f20f8-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="f20f8-107">Lors du réhébergement, un éditeur d'expressions personnalisé peut être développé pour prendre en charge IntelliSense ou un domaine d'expression simplifié.</span><span class="sxs-lookup"><span data-stu-id="f20f8-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="f20f8-108">L’intégration à Windows Communication Foundation (WCF) est devenue plus transparente grâce à l’utilisation des services de Workflow.</span><span class="sxs-lookup"><span data-stu-id="f20f8-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="f20f8-109">Les concepteurs d'activités personnalisées et l'arborescence d'éléments de modèle peuvent être utilisés pour améliorer les expériences au moment du design dans les concepteurs de workflow réhébergés.</span><span class="sxs-lookup"><span data-stu-id="f20f8-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f20f8-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f20f8-110">In This Section</span></span>

 [<span data-ttu-id="f20f8-111">Utilisation de concepteurs d’activités et de modèles d’activité personnalisés</span><span class="sxs-lookup"><span data-stu-id="f20f8-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="f20f8-112">Explique comment créer de nouveaux concepteurs d'activités et modèles d'activité personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f20f8-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="f20f8-113">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="f20f8-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="f20f8-114">Décrit comment réhéberger le [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] en dehors de Visual Studio et comment afficher les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="f20f8-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="f20f8-115">Utilisation d’un éditeur d’expressions personnalisé</span><span class="sxs-lookup"><span data-stu-id="f20f8-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="f20f8-116">Décrit comment implémenter un éditeur d’expressions personnalisé à utiliser avec les concepteurs de workflow réhébergés en dehors de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f20f8-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="f20f8-117">Reference</span><span class="sxs-lookup"><span data-stu-id="f20f8-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="f20f8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f20f8-118">See also</span></span>

- [<span data-ttu-id="f20f8-119">Extension de Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f20f8-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="f20f8-120">Concepteur</span><span class="sxs-lookup"><span data-stu-id="f20f8-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="f20f8-121">Concepteurs d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="f20f8-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="f20f8-122">Réhébergement du concepteur</span><span class="sxs-lookup"><span data-stu-id="f20f8-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
