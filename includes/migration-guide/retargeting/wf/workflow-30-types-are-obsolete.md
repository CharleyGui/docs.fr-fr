---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617252"
---
### <a name="workflow-30-types-are-obsolete"></a>Les types WorkFlow 3.0 sont obsolètes

#### <a name="details"></a>Détails

Les API WWF (Windows Workflow Foundation) 3.0 (celles de l’espace de noms System.Workflow) sont désormais obsolètes.

#### <a name="suggestion"></a>Suggestion

Les nouvelles API de WWF 4.0 (celles de System.Activities) doivent être utilisées à la place. Vous pouvez consulter un exemple d’utilisation des nouvelles API [ici](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) et obtenir une aide [ici](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5). Étant donné que les API WWF 3.0 sont toujours prises en charge, vous pouvez également les utiliser et éviter l’avertissement au moment de la génération en le supprimant ou en utilisant un compilateur plus ancien.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4,5         |
| Type    | Reciblage |
