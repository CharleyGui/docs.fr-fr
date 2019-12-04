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
# <a name="customizing-the-workflow-design-experience"></a>Personnalisation de l'expérience de conception de workflow

Les scénarios de conception d’activités personnalisées et de réhébergement de Windows Concepteur de flux de travail ont été considérablement simplifiés dans .NET Framework 4. Le développement et le déploiement sont maintenant à la fois plus facile et plus souple. La principale modification de l’infrastructure est que le nouveau modèle de programmation de concepteur d’activités repose sur Windows Presentation Foundation (WPF). Cela vous donne la possibilité de définir des concepteurs d’activités de façon déclarative et de réhéberger les Concepteur de flux de travail dans d’autres applications avec une comparaison simple. Lors du réhébergement, un éditeur d'expressions personnalisé peut être développé pour prendre en charge IntelliSense ou un domaine d'expression simplifié. L’intégration à Windows Communication Foundation (WCF) est devenue plus transparente grâce à l’utilisation des services de Workflow. Les concepteurs d'activités personnalisées et l'arborescence d'éléments de modèle peuvent être utilisés pour améliorer les expériences au moment du design dans les concepteurs de workflow réhébergés.

## <a name="in-this-section"></a>Dans cette section

 [Utilisation de concepteurs d’activités et de modèles d’activité personnalisés](using-custom-activity-designers-and-templates.md)

 Explique comment créer de nouveaux concepteurs d'activités et modèles d'activité personnalisés.

 [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)

 Décrit comment réhéberger les Concepteur de flux de travail Windows en dehors de Visual Studio et comment afficher les erreurs de validation.

 [Utilisation d’un éditeur d’expressions personnalisé](using-a-custom-expression-editor.md)

 Décrit comment implémenter un éditeur d’expressions personnalisé à utiliser avec les concepteurs de workflow réhébergés en dehors de Visual Studio 2010.

## <a name="reference"></a>Reference

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Voir aussi

- [Extension de Windows Workflow Foundation](extend.md)
- [Concepteur](./samples/designer.md)
- [Concepteurs d’activités personnalisées](./samples/custom-activity-designers.md)
- [Réhébergement du concepteur](./samples/designer-rehosting.md)
