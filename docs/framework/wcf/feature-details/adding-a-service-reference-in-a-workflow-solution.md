---
title: Ajout d'une référence de service dans une solution de workflow
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 1b4cc16d3bd85c28ac7267e88ae0a714620c9861
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557056"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Ajouter une référence de service dans une solution de workflow

L'ajout d'une référence de service dans une application de workflow fonctionne de façon légèrement différente que dans une application WCF normale. Lorsque vous sélectionnez **Ajouter**une  >  **référence de service** et spécifiez l’URL du service, les métadonnées sont téléchargées et des activités personnalisées qui vous permettent d’appeler ce service WCF ou le service de flux de travail WCF sont générées. Après l'ajout d'une référence de service, régénérez la solution pour que les activités générées soient construites. Celles-ci vont ensuite apparaître dans la boîte à outils du concepteur de workflow. Cela ne fonctionne que si vous ajoutez une référence de service dans une solution de Workflow. La diffusion Web suivante montre comment ajouter une référence de service dans d’autres types de projets : [appel d’un service WCF à partir d’un flux de travail dans un projet Web](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

L'ajout de deux ou plus références de service aux services qui contiennent le même nom d'opération entraîne un problème. Les activités générées vont appeler uniquement la première opération de service. Pour contourner ce problème, renommez les opérations de service afin qu’elles soient différentes ou modifiez le nom de la configuration du point de terminaison au sein de chaque activité générée.

## <a name="see-also"></a>Voir aussi

- [Services de workflow](workflow-services.md)
- [Appel d'un service WCF à partir d'un workflow dans un projet Web](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
